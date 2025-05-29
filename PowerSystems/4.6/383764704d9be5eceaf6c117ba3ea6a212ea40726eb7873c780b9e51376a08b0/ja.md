```julia
get_output_active_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HybridSystem`](@ref) の `output_active_power_limits` を取得します。
