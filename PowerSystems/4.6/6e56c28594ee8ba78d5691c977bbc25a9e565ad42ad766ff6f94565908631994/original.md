```julia
get_reactive_power_limits(
    value::PowerSystems.HydroEnergyReservoir
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HydroEnergyReservoir`](@ref) `reactive_power_limits`.
