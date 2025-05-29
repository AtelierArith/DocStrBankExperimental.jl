```julia
add_time_series!(
    sys::PowerSystems.System,
    components,
    time_series::InfrastructureSystems.TimeSeriesData;
    features...
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Add the same time series data to multiple components.

This function stores a single copy of the data. Each component will store a reference to that data. This is significantly more efficent than calling `add_time_series!` for each component individually with the same data because in this case, only one time series array is stored.

Throws ArgumentError if a component is not stored in the system.
