```julia
get_reactive_power_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HydroDispatch`](@ref) の `reactive_power_limits` を取得します。
