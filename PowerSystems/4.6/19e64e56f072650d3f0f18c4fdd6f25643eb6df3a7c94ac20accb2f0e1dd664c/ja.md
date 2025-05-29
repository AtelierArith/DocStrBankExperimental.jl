```julia
get_valve_position_limits(
    value::PowerSystems.TGTypeI
) -> @NamedTuple{min::Float64, max::Float64}

```

[`TGTypeI`](@ref) の `valve_position_limits` を取得します。
