```julia
add_time_series!(
    sys::PowerSystems.System,
    component::PowerSystems.Component,
    time_series::InfrastructureSystems.TimeSeriesData;
    features...
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Add time series data to a component.

Throws ArgumentError if the component is not stored in the system.
