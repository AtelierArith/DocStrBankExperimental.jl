```julia
get_time_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`HydroPumpedStorage`](@ref) の `time_limits_pump` を取得します。
