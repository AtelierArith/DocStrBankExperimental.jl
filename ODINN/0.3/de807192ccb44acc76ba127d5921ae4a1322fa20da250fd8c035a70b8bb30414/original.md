Constructor for the `Parameters` type. Since some of the subtypes of parameters are defined in different packages of the ODINN ecosystem, this constructor will call the constructors of the different subtypes and return a `Parameters` object with the corresponding subtypes.  The `Parameters` mutable struct is defined in `Sleipnir.jl` using abstract types, which are later on defined in the different packages of the ODINN ecosystem.

```
Parameters(;
        physical::PhysicalParameters = PhysicalParameters(),
        simulation::SimulationParameters = SimulationParameters(),
        solver::SolverParameters = SolverParameters(),
        hyper::Hyperparameters = Hyperparameters(),
        UDE::UDEparameters = UDEparameters()
        inversion::InversionParameters = InversionParameters()
        )
```

# Keyword arguments

  * `physical::PhysicalParameters`: Physical parameters for the simulation.
  * `simulation::SimulationParameters`: Parameters related to the simulation setup.
  * `solver::SolverParameters`: Parameters for the solver configuration.
  * `hyper::Hyperparameters`: Hyperparameters for the model.
  * `UDE::UDEparameters`: Parameters specific to the UDE (Universal Differential Equation).
  * `inversion::InversionParameters`: Parameters for inversion processes.
