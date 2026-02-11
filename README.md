# Unidad-2_Practica-1
    class Program
    {
    static void Main(string[] args)
    {
        int Personas = 0, edad = 0;
        string nombre;

        Validar cantidad de personas
        while (true)
        {
            try
            {
                Console.Write("Ingrese la cantidad de personas a registrar (mínimo 1): ");
                Personas = int.Parse(Console.ReadLine());

                if (Personas < 1)
                {
                    Console.WriteLine("Debe ingresar un número mayor o igual a 1.\n");
                    continue;
                }

                break;
            }
            catch (FormatException)
            {
                Console.WriteLine("Entrada inválida. Debe ingresar un número entero.\n");
            }
        }

        List<string> nombres = new List<string>();
        List<int> edades = new List<int>();

        // Solicitar datos
        for (int i = 0; i < Personas; i++)
        {
            Console.WriteLine($"\nPersona #{i + 1}");

            Console.Write("Nombre: ");
            nombre = Console.ReadLine();
            nombres.Add(nombre);

            // Validar edad con try-catch
            while (true)
            {
                try
                {
                    Console.Write("Edad: ");
                    edad = int.Parse(Console.ReadLine());

                    if (edad < 0)
                    {
                        Console.WriteLine("La edad no puede ser negativa.\n");
                        continue;
                    }

                    break;
                }
                catch (FormatException)
                {
                    Console.WriteLine("Entrada inválida. Debe ingresar un número entero.\n");
                }
            }

            edades.Add(edad);
        }

        // Caso especial: una sola persona
        if (Personas == 1)
        {
            Console.WriteLine("\n--- Resultado ---");
            Console.WriteLine($"Nombre: {nombres[0]}");

            if (edades[0] >= 18)
                Console.WriteLine("Es mayor de edad.");
            else
                Console.WriteLine("Es menor de edad.");

            return;
        }

        // Caso general
        Console.WriteLine("\n--- Lista Mayores ---");
        for (int i = 0; i < nombres.Count; i++)
        {
            if (edades[i] >= 18)
            {
                Console.WriteLine($"{nombres[i]} - {edades[i]} años");
            }   
        }
        Console.WriteLine("\n--- Lista menores ---");
        for (int i = 0; i < nombres.Count; i++)
        {
            if (edades[i] < 18)
            {
                Console.WriteLine($"{nombres[i]} - {edades[i]} años");
            }
        }
    }
}
