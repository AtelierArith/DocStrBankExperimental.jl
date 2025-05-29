```julia
get_reactive_power_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HydroPumpedStorage`](@ref) の `reactive_power_limits` を取得します。
