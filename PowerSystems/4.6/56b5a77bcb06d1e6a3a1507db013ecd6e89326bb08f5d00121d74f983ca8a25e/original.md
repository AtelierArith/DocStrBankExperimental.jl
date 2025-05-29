```julia
mutable struct MarketBidCost <: PowerSystems.OperationalCost
```

  * `no_load_cost::Union{Nothing, Float64, InfrastructureSystems.TimeSeriesKey}`: No load cost
  * `start_up::Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesKey}`: Start-up cost at different stages of the thermal cycle as the unit cools after a     shutdown (e.g., *hot*, *warm*, or *cold* starts). Warm is also referred to as     intermediate in some markets. Can also accept a single value if there is only one     start-up cost
  * `shut_down::Union{Float64, InfrastructureSystems.TimeSeriesKey}`: Shut-down cost
  * `incremental_offer_curves::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}`: Sell Offer Curves data, which can be a time series of `PiecewiseStepData` or a     [`CostCurve`](@ref) of [`PiecewiseIncrementalCurve`](@ref)
  * `decremental_offer_curves::Union{Nothing, InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, InfrastructureSystems.TimeSeriesKey}`: Buy Offer Curves data, which can be a time series of `PiecewiseStepData` or a     [`CostCurve`](@ref) of [`PiecewiseIncrementalCurve`](@ref)
  * `incremental_initial_input::Union{Nothing, InfrastructureSystems.TimeSeriesKey}`: If using a time series for incremental*offer*curves, this is a time series of `Float64` representing the `initial_input`
  * `decremental_initial_input::Union{Nothing, InfrastructureSystems.TimeSeriesKey}`: If using a time series for decremental*offer*curves, this is a time series of `Float64` representing the `initial_input`
  * `ancillary_service_offers::Vector{PowerSystems.Service}`: Bids for the ancillary services

```
MarketBidCost(no_load_cost, start_up, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
MarketBidCost(; no_load_cost, start_up, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
MarketBidCost(no_load_cost, start_up::Real, shut_down, incremental_offer_curves, decremental_offer_curves, ancillary_service_offers)
```

An operating cost for market bids of energy and ancilliary services for any asset. Compatible with most US Market bidding mechanisms that support demand and generation side.
