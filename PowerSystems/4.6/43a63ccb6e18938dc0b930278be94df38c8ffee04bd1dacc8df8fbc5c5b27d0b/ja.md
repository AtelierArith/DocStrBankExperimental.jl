```julia
get_decremental_offer_curves(
    value::PowerSystems.MarketBidCost
) -> Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}

```

[`MarketBidCost`](@ref) `decremental_offer_curves`を取得します。
