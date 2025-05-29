```julia
make_market_bid_curve(
    data::InfrastructureSystems.PiecewiseStepData,
    initial_input::Float64;
    power_units,
    input_at_zero
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

Make a CostCurve{PiecewiseIncrementalCurve} suitable for inclusion in a MarketBidCost from the FunctionData that might be used to store such a cost curve in a time series.
