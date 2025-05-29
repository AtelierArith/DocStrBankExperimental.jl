```julia
struct PLR_Simulation
```

Type containing the parameters and results of a PLR simulation.

# Fields

  * `params::SlottedRandomAccess.PLR_SimulationParameters`: Parameters used for the simulation
  * `results::StructArrays.StructArray{SlottedRandomAccess.PLR_Simulation_Point}`: Results of the simulation
  * `scatter_kwargs::Dict{Symbol, Any}`: The list of keyword arguments passed to the scatter call for plotting

# Constructors

```
PLR_Simulation(load::AbstractVector; kwargs...)
```

Create a `PLR_Simulation` object by simply providing the load vector. This forwards all the `kwargs` to the [`PLR_SimulationParameters`](@ref) constructor.

```
PLR_Simulation(load::AbstractVector, params::PLR_SimulationParameters; scatter_kwargs = Dict{Symbol, Any}())
```

This constructor permits to provide both the load and the `params` field directly as positional arguments. The custom keyword arguments to pass to the `scatter` call from PlotlyBase can be provided using the `scatter_kwargs` keyword argument, which defaults to an empty `Dict`.

See also: [`PLR_SimulationParameters`](@ref)
