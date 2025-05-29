```julia
set_decremental_initial_input!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Set the `decremental_initial_input` for a `StaticInjection` device with a `MarketBidCost` to either a scalar or a time series.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: Static injection device
  * `time_series_data::Union{Float64, IS.TimeSeriesData},`: the data. If a time series, must be of eltype `Float64`.
