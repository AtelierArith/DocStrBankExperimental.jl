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

Accepts a single `start_up` value to use as the `hot` value, with `warm` and `cold` set to `0.0`.
