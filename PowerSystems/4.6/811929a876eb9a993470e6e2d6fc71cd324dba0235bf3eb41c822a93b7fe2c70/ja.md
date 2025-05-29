```julia
get_no_load_cost(
    value::PowerSystems.MarketBidCost
) -> Union{Nothing, Float64, InfrastructureSystems.TimeSeriesKey}

```

[`MarketBidCost`](@ref) の `no_load_cost` を取得します。
