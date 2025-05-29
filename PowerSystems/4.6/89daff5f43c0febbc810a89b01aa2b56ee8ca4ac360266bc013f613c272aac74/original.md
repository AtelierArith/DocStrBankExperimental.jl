```julia
make_market_bid_curve(
    powers::Vector{Float64},
    marginal_costs::Vector{Float64},
    initial_input::Float64;
    power_units,
    input_at_zero
) -> InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}

```

Make a CostCurve{PiecewiseIncrementalCurve} suitable for inclusion in a MarketBidCost from a vector of power values, a vector of marginal costs, a float of initial input, and an optional units system and input at zero.

# Examples

```julia
mbc = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0)
mbc2 = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0; input_at_zero = 10.0)
mbc3 = make_market_bid_curve([0.0, 100.0, 105.0, 120.0, 130.0], [25.0, 26.0, 28.0, 30.0], 10.0; power_inputs = UnitSystem.NATURAL_UNITS)
```
