```julia
get_reactive_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HybridSystem`](@ref) の `reactive_power_limits` を取得します。
