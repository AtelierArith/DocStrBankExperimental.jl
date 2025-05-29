```julia
MarketBidCost(
    no_load_cost,
    start_up::Real,
    shut_down;
    incremental_offer_curves,
    decremental_offer_curves,
    incremental_initial_input,
    decremental_initial_input,
    ancillary_service_offers
) -> Any

```

単一の `start_up` 値を受け入れ、`hot` 値として使用し、`warm` と `cold` は `0.0` に設定されます。
