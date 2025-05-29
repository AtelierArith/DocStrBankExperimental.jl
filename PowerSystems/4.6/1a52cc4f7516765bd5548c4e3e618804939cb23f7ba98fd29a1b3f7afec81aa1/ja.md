```julia
get_phase_angle_limits(
    value::PowerSystems.PhaseShiftingTransformer
) -> @NamedTuple{min::Float64, max::Float64}

```

[`PhaseShiftingTransformer`](@ref) の `phase_angle_limits` を取得します。
