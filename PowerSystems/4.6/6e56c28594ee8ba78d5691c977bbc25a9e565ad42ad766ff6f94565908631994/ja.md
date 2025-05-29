```julia
get_reactive_power_limits(
    value::PowerSystems.HydroEnergyReservoir
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HydroEnergyReservoir`](@ref) の `reactive_power_limits` を取得します。
