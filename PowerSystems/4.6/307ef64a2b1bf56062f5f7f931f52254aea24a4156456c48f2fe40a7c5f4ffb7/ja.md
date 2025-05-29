```julia
get_input_active_power_limits(
    value::PowerSystems.HybridSystem
) -> Union{Nothing, NamedTuple{(:min, :max), <:Tuple{Any, Any}}}

```

[`HybridSystem`](@ref) `input_active_power_limits`を取得します。
