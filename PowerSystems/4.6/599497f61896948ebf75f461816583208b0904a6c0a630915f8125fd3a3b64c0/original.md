```julia
get_reactive_power_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`ThermalMultiStart`](@ref) `reactive_power_limits`.
