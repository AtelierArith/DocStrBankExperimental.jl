```julia
get_incremental_offer_curves(
    value::PowerSystems.MarketBidCost
) -> Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}

```

[`MarketBidCost`](@ref) `incremental_offer_curves`を取得します。
