```julia
make_market_bid_curve(
    powers::Vector{Float64},
    marginal_costs::Vector{Float64},
    initial_input::Float64;
    power_units,
    input_at_zero
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

ベクトルの電力値、ベクトルの限界コスト、初期入力の浮動小数点数、およびオプションの単位システムとゼロでの入力から、MarketBidCostに含めるのに適したCostCurve{PiecewiseIncrementalCurve}を作成します。

# 例

```julia
mbc = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0)
mbc2 = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0; input_at_zero = 10.0)
mbc3 = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0; power_inputs = UnitSystem.NATURAL_UNITS)
```
