```julia
get_active_power_limits(
    value::PowerSystems.HydroDispatch
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

[`HydroDispatch`](@ref) の `active_power_limits` を取得します。
