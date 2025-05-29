```julia
MarketBidCost(
    no_load_cost::Union{Nothing, Float64, InfrastructureSystems.TimeSeriesKey},
    start_up::Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesKey},
    shut_down::Integer,
    incremental_offer_curves,
    decremental_offer_curves,
    incremental_initial_input,
    decremental_initial_input,
    ancillary_service_offers
) -> PowerSystems.MarketBidCost

```

Auxiliary constructor for shut_down::Integer
