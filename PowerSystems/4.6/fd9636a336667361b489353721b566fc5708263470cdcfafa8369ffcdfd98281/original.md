```julia
get_decremental_offer_curves(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, TimeSeries.TimeArray}

```

Retrieve the `decremental_offer_curves` for a `StaticInjection` device with a `MarketBidCost`. If this field is a time series, the user may specify `start_time` and `len` and the function returns a `TimeArray` of `Float64`s; if the field is not a time series, the function returns a single `Float64` or `Nothing`.
