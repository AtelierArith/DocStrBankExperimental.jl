```julia
get_ramp_limits_pump(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`HydroPumpedStorage`](@ref) の `ramp_limits_pump` を取得します。
