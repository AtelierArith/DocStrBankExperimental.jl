```julia
get_rectifier_firing_angle(
    value::PowerSystems.TwoTerminalVSCDCLine
) -> @NamedTuple{min::Float64, max::Float64}

```

[`TwoTerminalVSCDCLine`](@ref) の `rectifier_firing_angle` を取得します。
