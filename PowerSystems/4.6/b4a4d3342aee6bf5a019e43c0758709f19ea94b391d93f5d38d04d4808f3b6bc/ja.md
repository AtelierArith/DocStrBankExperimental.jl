```julia
get_ramp_limits(
    value::PowerSystems.HydroPumpedStorage
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`HydroPumpedStorage`](@ref) の `ramp_limits` を取得します。
