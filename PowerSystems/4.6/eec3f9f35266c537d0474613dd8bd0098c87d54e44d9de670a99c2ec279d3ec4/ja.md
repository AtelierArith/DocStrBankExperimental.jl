```julia
get_valve_position_limits(
    value::PowerSystems.SteamTurbineGov1
) -> @NamedTuple{min::Float64, max::Float64}

```

[`SteamTurbineGov1`](@ref) の `valve_position_limits` を取得します。
