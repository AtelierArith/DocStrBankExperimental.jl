```julia
get_reactive_power_limits(
    value::PowerSystems.EnergyReservoirStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`EnergyReservoirStorage`](@ref) `reactive_power_limits`.
