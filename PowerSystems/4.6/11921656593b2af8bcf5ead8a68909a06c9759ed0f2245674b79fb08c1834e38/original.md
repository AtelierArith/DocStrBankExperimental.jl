```julia
set_variable_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    data::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesData},
    power_units::InfrastructureSystems.UnitSystemModule.UnitSystem
)

```

Set the incremental variable cost bid for a `StaticInjection` device with a `MarketBidCost`.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: Static injection device
  * `time_series_data::Union{Nothing, IS.TimeSeriesData, CostCurve{PiecewiseIncrementalCurve}},`: the data. If using a time series, must be of eltype `PiecewiseStepData`. `PiecewiseIncrementalCurve` is only accepted for single CostCurve and not accepted for time series data.
  * `power_units::UnitSystem`: Units to be used for data. Must be NATURAL_UNITS.
