```julia
get_reactive_power_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`ThermalMultiStart`](@ref) の `reactive_power_limits` を取得します。
