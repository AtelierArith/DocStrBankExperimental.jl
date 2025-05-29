```julia
get_decremental_initial_input(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Nothing, TimeSeries.TimeArray}

```

Retrieve the `decremental_initial_input` for a `StaticInjection` device with a `MarketBidCost`.
