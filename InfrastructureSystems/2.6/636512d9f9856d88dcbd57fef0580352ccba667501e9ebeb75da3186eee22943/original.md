```julia
get_initial_input(
    cost::InfrastructureSystems.ProductionVariableCostCurve
) -> Union{Nothing, Float64}

```

Get the `initial_input` field of this `ProductionVariableCostCurve`'s `ValueCurve` (not defined for input-output data)
