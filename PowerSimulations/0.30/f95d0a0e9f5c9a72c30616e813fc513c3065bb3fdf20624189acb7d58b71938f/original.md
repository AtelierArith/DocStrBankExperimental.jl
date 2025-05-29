```julia
show_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString;
    ...
)
show_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString,
    filter_func::Union{Nothing, Function};
    wall_time,
    kwargs...
)

```

```
show_recorder_events(
    ::Type{T},
    filename::AbstractString,
    filter_func::Union{Nothing, Function} = nothing;
    wall_time = false,
    kwargs...,
) where {T <: IS.AbstractRecorderEvent}
```

Show the events of type T in a recorder file.

# Arguments

  * `::Type{T}`: Recorder event type
  * `filename::AbstractString`: recorder filename
  * `filter_func::Union{Nothing, Function} = nothing`: Optional function that accepts an event of type T and returns a Bool. Apply this function to each event and only return events where the result is true.
  * `wall_time = false`: If true, show the wall_time timestamp.
