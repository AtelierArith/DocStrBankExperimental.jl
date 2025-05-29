```julia
get_angle_limits(
    value::PowerSystems.MonitoredLine
) -> @NamedTuple{min::Float64, max::Float64}

```

[`MonitoredLine`](@ref) の `angle_limits` を取得します。
