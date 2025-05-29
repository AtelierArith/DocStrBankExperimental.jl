```julia
get_time_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`HydroPumpedStorage`](@ref) の `time_limits` を取得します。
