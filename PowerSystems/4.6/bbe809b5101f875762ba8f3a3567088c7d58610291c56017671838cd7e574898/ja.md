```julia
get_reactive_power_limits(
    value::PowerSystems.EnergyReservoirStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`EnergyReservoirStorage`](@ref) の `reactive_power_limits` を取得します。
