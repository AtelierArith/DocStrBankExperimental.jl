```julia
get_active_power_limits(
    value::PowerSystems.HydroPumpedStorage
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

[`HydroPumpedStorage`](@ref) の `active_power_limits` を取得します。
