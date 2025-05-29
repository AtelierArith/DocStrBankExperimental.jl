```julia
get_valve_position_limits(
    value::PowerSystems.GeneralGovModel
) -> @NamedTuple{min::Float64, max::Float64}

```

[`GeneralGovModel`](@ref) `valve_position_limits`を取得します。
