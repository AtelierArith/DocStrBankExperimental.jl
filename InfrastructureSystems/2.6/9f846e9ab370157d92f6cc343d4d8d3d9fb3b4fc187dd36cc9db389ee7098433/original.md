```julia
Scenarios(
    src::InfrastructureSystems.Scenarios,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.Scenarios

```

Construct Scenarios that shares the data from an existing instance.

This is useful in cases where you want a component to use the same time series data for two different attributes.
