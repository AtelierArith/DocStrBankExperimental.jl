```julia
get_reactive_power_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HydroPumpedStorage`](@ref) `reactive_power_limits`.
