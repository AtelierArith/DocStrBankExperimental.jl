```julia
get_reactive_power_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HydroPumpedStorage`](@ref) `reactive_power_limits_pump`.
