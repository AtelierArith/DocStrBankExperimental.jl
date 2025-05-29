```julia
get_power_trajectory(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, NamedTuple{(:startup, :shutdown), <:Tuple{Any, Any}}}

```

[`ThermalMultiStart`](@ref) `power_trajectory`を取得します。
