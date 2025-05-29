```julia
list_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString
) -> Vector{T} where T<:InfrastructureSystems.AbstractRecorderEvent
list_recorder_events(
    ::Type{T<:InfrastructureSystems.AbstractRecorderEvent},
    filename::AbstractString,
    filter_func::Union{Nothing, Function}
) -> Vector{T} where T<:InfrastructureSystems.AbstractRecorderEvent

```

Return the events of type T in filename.

# Arguments

  * `T`: event type
  * `filename::AbstractString`: filename containing recorder events
  * `filter_func::Union{Nothing, Function} = nothing`: Optional function that accepts an event of type T and returns a Bool. Apply this function to each event and only return events where the result is true.
