```julia
set_service_bid!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    service::PowerSystems.Service,
    time_series_data::InfrastructureSystems.TimeSeriesData,
    power_units::InfrastructureSystems.UnitSystemModule.UnitSystem
)

```

Adds service bids time-series data to the MarketBidCost.

# Arguments

  * `sys::System`: PowerSystem System
  * `component::StaticInjection`: Static injection device
  * `service::Service,`: Service for which the device is eligible to contribute
  * `time_series_data::IS.TimeSeriesData`: TimeSeriesData
