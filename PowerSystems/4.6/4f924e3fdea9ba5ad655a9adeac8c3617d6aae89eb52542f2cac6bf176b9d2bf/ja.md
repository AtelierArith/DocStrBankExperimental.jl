```julia
make_market_bid_curve(
    data::InfrastructureSystems.PiecewiseStepData,
    initial_input::Float64;
    power_units,
    input_at_zero
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

MarketBidCostに含めるのに適したCostCurve{PiecewiseIncrementalCurve}をFunctionDataから作成します。これは、時系列でそのようなコスト曲線を保存するために使用される可能性があります。
