```julia
get_incremental_initial_input(
    device::PowerSystems.StaticInjection,
    cost::PowerSystems.MarketBidCost;
    start_time,
    len
) -> Union{Nothing, TimeSeries.TimeArray}

```

`StaticInjection`デバイスの`MarketBidCost`に対する`incremental_initial_input`を取得します。
