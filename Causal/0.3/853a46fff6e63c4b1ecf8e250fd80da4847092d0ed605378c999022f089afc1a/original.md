```julia
mutable struct Simulation{MD, CK}
```

Constructs a `Simulation` object for the simulation of `model`. The `Simulation` object is used to monitor the state of the simulation of the `model`. `simdir` is the path of the directory into which the simulation files(log, data files etc.) are recorded. `simname` is the name of the `Simulation` and `simprefix` is the prefix of the name of the `Simulation`. `logger` is used to log the simulation steps of the `model`. See also: [`Model`](@ref), [`Logging`](https://docs.julialang.org/en/v1/stdlib/Logging/)

# Fields

  * `model::Any`: Model to be simulated
  * `clock::Any`: Simulation clock
  * `path::String`: Path to which simulation files are recorded
  * `logger::Union{Base.CoreLogging.ConsoleLogger, Base.CoreLogging.SimpleLogger}`: Simulation logger
  * `state::Symbol`: Simulation state
  * `retcode::Symbol`: Simulation return code
  * `name::String`: Simulation name
