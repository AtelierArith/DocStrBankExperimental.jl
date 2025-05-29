```julia
SingleTimeSeries(
    src::InfrastructureSystems.SingleTimeSeries,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.SingleTimeSeries

```

Construct SingleTimeSeries that shares the data from an existing instance.

This is useful in cases where you want a component to use the same time series data for two different attribtues.
