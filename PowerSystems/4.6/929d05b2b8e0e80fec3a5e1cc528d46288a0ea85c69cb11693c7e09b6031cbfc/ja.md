```julia
get_ramp_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, NamedTuple{(:up, :down), <:Tuple{Any, Any}}}

```

[`HydroDispatch`](@ref) の `ramp_limits` を取得します。
