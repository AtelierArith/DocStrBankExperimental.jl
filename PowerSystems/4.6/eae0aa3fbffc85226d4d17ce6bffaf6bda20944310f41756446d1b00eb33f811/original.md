```julia
get_time_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

Get [`HydroPumpedStorage`](@ref) `time_limits_pump`.
