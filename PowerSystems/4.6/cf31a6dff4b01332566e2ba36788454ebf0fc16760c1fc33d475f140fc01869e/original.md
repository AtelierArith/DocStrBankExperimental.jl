```julia
get_reactive_power_limits(
    value::PowerSystems.ThermalStandard
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`ThermalStandard`](@ref) `reactive_power_limits`.
