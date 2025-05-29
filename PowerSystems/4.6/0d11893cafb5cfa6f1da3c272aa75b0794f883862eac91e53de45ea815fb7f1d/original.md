```julia
get_shut_down(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Float64, TimeSeries.TimeArray}

```

Retrieve the shutdown cost data for a `StaticInjection` device with a `MarketBidCost`. If this field is a time series, the user may specify `start_time` and `len` and the function returns a `TimeArray` of `Float64`s; if the field is not a time series, the function returns a single `Float64`.
