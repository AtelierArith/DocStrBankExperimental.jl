```julia
get_reactive_power_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HydroDispatch`](@ref) `reactive_power_limits`.
