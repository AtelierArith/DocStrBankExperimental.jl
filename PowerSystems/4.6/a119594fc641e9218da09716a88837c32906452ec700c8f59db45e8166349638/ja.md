```julia
get_ramp_limits(
    value::PowerSystems.HydroEnergyReservoir
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`HydroEnergyReservoir`](@ref) の `ramp_limits` を取得します。
