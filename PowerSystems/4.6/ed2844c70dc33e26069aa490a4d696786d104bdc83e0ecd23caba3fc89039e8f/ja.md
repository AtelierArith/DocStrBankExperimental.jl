```julia
MarketBidCost(
    no_load_cost::Float64,
    start_up::Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesKey},
    shut_down::Union{Float64, InfrastructureSystems.TimeSeriesKey},
    incremental_offer_curves,
    decremental_offer_curves,
    ancillary_service_offers
) -> PowerSystems.MarketBidCost

```

テストデータのための補助コンストラクタ
