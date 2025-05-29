```julia
set_start_up!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesData}
) -> Union{Float64, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

Set the startup cost for a `StaticInjection` device with a `MarketBidCost` to either a single number, a single `StartUpStages`, or a time series.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: Static injection device
  * `data::Union{Float64, StartUpStages, IS.TimeSeriesData},`: the data. If a time series, must be of eltype `NTuple{3, Float64}` – to represent a single value in a time series, use `(value, 0.0, 0.0)`.
