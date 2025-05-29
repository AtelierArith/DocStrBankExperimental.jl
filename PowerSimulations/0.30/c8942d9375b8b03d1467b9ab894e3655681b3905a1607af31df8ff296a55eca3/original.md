```julia
show_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString;
    ...
)
show_simulation_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    output_dir::AbstractString,
    filter_func::Union{Nothing, Function};
    step,
    model,
    wall_time,
    kwargs...
)

```

```
show_simulation_events(
    ::Type{T},
    output_dir::AbstractString,
    filter_func::Union{Nothing,Function} = nothing;
    step = nothing,
    model = nothing,
    wall_time = false,
    kwargs...,
) where { T <: IS.AbstractRecorderEvent}
```

Show all simulation events of type T in a simulation output directory.

# Arguments

  * `::Type{T}`: Recorder event type
  * `output_dir::AbstractString`: Simulation output directory
  * `filter_func::Union{Nothing, Function} = nothing`: Refer to [`show_recorder_events`](@ref).
  * `step::Int = nothing`: Filter events by step. Required if model is passed.
  * `model::Int = nothing`: Filter events by model.
  * `wall_time = false`: If true, show the wall_time timestamp.
