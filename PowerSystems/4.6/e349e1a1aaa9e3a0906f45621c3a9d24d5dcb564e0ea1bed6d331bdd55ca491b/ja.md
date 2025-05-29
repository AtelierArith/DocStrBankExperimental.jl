```julia
get_input_active_power_limits(
    value::PowerSystems.EnergyReservoirStorage
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

[`EnergyReservoirStorage`](@ref) の `input_active_power_limits` を取得します。
