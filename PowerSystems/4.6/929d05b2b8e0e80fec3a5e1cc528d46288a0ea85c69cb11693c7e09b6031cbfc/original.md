```julia
get_ramp_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

Get [`HydroDispatch`](@ref) `ramp_limits`.
