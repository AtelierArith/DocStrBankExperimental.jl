```julia
get_inverter_tap_limits(
    value::PowerSystems.TwoTerminalVSCDCLine
) -> @NamedTuple{min::Float64, max::Float64}

```

Get [`TwoTerminalVSCDCLine`](@ref) `inverter_tap_limits`.
