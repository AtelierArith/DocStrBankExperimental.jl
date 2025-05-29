```julia
check_time_series_consistency(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
) -> Union{Nothing, Tuple{Any, Any}}

```

Checks time series in the system for inconsistencies.

For SingleTimeSeries, returns a Tuple of initial_timestamp and length.

This is a no-op for subtypes of Forecast because those are already guaranteed to be consistent.

Throws InfrastructureSystems.InvalidValue if any time series is inconsistent.
