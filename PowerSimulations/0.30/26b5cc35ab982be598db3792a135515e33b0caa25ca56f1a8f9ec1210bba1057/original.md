```julia
list_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString;
    ...
) -> Vector{T} where T<:PowerSimulations.AbstractSimulationStatusEvent
list_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function};
    step,
    model_name
) -> Vector{T} where T<:PowerSimulations.AbstractSimulationStatusEvent

```

```
list_simulation_events(
    ::Type{T},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function} = nothing;
    step = nothing,
    model = nothing,
) where {T <: IS.AbstractRecorderEvent}
```

List simulation events of type T in a simulation output directory.

# Arguments

  * `output_dir::AbstractString`: Simulation output directory
  * `filter_func::Union{Nothing, Function} = nothing`: Refer to [`show_simulation_events`](@ref).
  * `step::Int = nothing`: Filter events by step. Required if model is passed.
  * `model::Int = nothing`: Filter events by model.
