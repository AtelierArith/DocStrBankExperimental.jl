```julia
get_time_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

Get [`HydroPumpedStorage`](@ref) `time_limits`.
