```julia
set_shut_down!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, InfrastructureSystems.TimeSeriesData}
) -> Union{Float64, InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Set the shutdown cost for a `StaticInjection` device with a `MarketBidCost` to either a single number or a time series.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: Static injection device
  * `data::Union{Float64, IS.TimeSeriesData},`: the data. If a time series, must be of eltype `Float64`.
