```julia
get_power_trajectory(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, NamedTuple{(:startup, :shutdown), <:Tuple{Any, Any}}}

```

Get [`ThermalMultiStart`](@ref) `power_trajectory`.
