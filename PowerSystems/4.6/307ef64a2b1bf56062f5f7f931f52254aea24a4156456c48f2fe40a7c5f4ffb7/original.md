```julia
get_input_active_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HybridSystem`](@ref) `input_active_power_limits`.
