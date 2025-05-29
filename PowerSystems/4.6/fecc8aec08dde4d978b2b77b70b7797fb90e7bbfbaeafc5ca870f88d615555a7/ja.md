```julia
get_reactive_power_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HydroPumpedStorage`](@ref) の `reactive_power_limits_pump` を取得します。
