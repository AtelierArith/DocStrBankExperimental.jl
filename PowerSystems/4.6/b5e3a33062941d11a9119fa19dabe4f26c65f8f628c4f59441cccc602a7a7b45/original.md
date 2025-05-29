```julia
get_no_load_cost(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Nothing, Float64, TimeSeries.TimeArray}

```

Retrieve the no-load cost data for a `StaticInjection` device with a `MarketBidCost`. If this field is a time series, the user may specify `start_time` and `len` and the function returns a `TimeArray` of `Float64`s; if the field is not a time series, the function returns a single `Float64` or `Nothing`.
