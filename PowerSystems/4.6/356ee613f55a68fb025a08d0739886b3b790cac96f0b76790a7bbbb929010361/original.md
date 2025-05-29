```julia
set_variable_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.ReserveDemandCurve,
    data::Union{Nothing, InfrastructureSystems.TimeSeriesData}
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Adds energy market bids time-series to the ReserveDemandCurve.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::ReserveDemandCurve`: the curve
  * `time_series_data::IS.TimeSeriesData`: TimeSeriesData
