```julia
get_rectifier_tap_limits(
    value::PowerSystems.TwoTerminalVSCDCLine
) -> @NamedTuple{min::Float64, max::Float64}

```

[`TwoTerminalVSCDCLine`](@ref) の `rectifier_tap_limits` を取得します。
