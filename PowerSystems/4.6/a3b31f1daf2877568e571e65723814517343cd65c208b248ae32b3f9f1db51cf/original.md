```julia
remove_time_series!(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData},
    component::PowerSystems.Component,
    name::String
)

```

Remove the time series data for a component and time series type.
