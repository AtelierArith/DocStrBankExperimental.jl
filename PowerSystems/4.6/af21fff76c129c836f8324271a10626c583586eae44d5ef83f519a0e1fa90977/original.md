```julia
get_services_bid(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost,
    service::PowerSystems.Service;
    start_time,
    len
) -> TimeSeries.TimeArray

```

Return service bid time series data for a `StaticInjection` device with a `MarketBidCost`. The user may specify `start_time` and `len` and the function returns a `TimeArray` of `CostCurve`s.
