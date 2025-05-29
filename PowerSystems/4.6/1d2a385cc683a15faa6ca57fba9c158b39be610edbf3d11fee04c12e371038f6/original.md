```julia
get_start_up(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, TimeSeries.TimeArray}

```

Retrieve the startup cost data for a `StaticInjection` device with a `MarketBidCost`. If this field is a time series, the user may specify `start_time` and `len` and the function returns a `TimeArray` of `StartUpStages`s; if the field is not a time series, the function returns a single `StartUpStages`.
