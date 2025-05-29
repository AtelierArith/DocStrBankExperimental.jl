```julia
get_ramp_limits(
    value::PowerSystems.ThermalStandard
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`ThermalStandard`](@ref) の `ramp_limits` を取得します。
