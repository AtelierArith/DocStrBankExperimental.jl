```julia
get_reactive_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HybridSystem`](@ref) `reactive_power_limits`.
