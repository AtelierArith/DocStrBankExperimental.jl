```julia
get_reactive_power_limits(
    value::PowerSystems.ThermalStandard
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`ThermalStandard`](@ref) の `reactive_power_limits` を取得します。
