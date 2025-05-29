```julia
get_valve_position_limits(
    value::PowerSystems.IEEETurbineGov1
) -> @NamedTuple{min::Float64, max::Float64}

```

[`IEEETurbineGov1`](@ref) の `valve_position_limits` を取得します。
