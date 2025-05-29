```julia
get_initial_input(
    curve::Union{InfrastructureSystems.AverageRateCurve, InfrastructureSystems.IncrementalCurve}
) -> Union{Nothing, Float64}

```

Get the `initial_input` field of this `ValueCurve` (not defined for `InputOutputCurve`)
