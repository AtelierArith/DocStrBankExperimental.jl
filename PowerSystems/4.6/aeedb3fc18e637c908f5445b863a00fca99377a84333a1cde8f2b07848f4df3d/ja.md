```julia
get_ramp_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`ThermalMultiStart`](@ref) の `ramp_limits` を取得します。
