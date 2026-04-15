    internal class Sistema
    {
        static void Main(string[] args)
        {
            List<Empleado> empleados= new List<Empleado>();

            empleados.Add(new EmpleadoPorHora ("Maria","Por hora",  4 ,50000));
            empleados.Add(new EmpleadoTiempoCompleto("Ana","Tiempo completo",  70000));
            empleados.Add(new EmpleadoTiempoCompleto("Ana","Tiempo completo" , 1000));
            empleados.Add(new EmpleadoFreelance("Sebastian", "Freelance", 90000));
            empleados.Add(new EmpleadoPorHora("Popcat", "Por hora",60, 500));
            empleados.Add(new Gerente("Jade", "Gerente", 10000000, 100 ));
            empleados.Add(new EmpleadoAdministrativo("ivan", "Administrativo", 100000, 100));



            foreach (Empleado e in empleados)
            {
                e.mostrarInformacion();

                double salario = e.CalcularSalario();
                Console.WriteLine("Salario: " + salario);

                if (e is IBonificacion)
                {
                    IBonificacion b = (IBonificacion)e;
                    double bonificacion = b.CalcularBonificacion();

                    Console.WriteLine("Bonificación: " + bonificacion);
                    Console.WriteLine("Total: " + (salario + bonificacion));
                }
                else
                {
                    Console.WriteLine("Bonificación: No aplica");
                    Console.WriteLine("Total: " + salario);
                }

                Console.WriteLine("----------------------");
            }

        }
    }
