```julia
get_variable_cost(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey, TimeSeries.TimeArray}

```

Retrieve the variable cost bid for a `StaticInjection` device with a `MarketBidCost`. If any of the relevant fields (`incremental_offer_curves`, `initial_input`, `no_load_cost`) are time series, the user may specify `start_time` and `len` and the function returns a `TimeArray` of `CostCurve`s; if the field is not a time series, the function returns a single `CostCurve`.
