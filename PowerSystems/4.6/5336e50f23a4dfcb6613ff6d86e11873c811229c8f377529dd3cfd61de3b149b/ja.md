```julia
get_active_power_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

[`HydroPumpedStorage`](@ref) の `active_power_limits_pump` を取得します。
