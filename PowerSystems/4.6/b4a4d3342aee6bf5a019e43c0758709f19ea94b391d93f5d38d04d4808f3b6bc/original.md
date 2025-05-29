```julia
get_ramp_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

Get [`HydroPumpedStorage`](@ref) `ramp_limits`.
