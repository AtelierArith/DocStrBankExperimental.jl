```julia
get_output_active_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

Get [`HybridSystem`](@ref) `output_active_power_limits`.
