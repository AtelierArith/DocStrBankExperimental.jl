```
present_value(model,contract,current_time=0.0)
present_value(model,projection,current_time=0.0)
```

Return the value of the contract as corresponding with the valuation assumptions embedded in the `model` for the given contract or projection with `CashflowProjection` kind.

# Examples

```julia
m = Equity.BlackScholesMerton(0.01, 0.02, 0.15)

a = Option.EuroCall(CommonEquity(), 1.0, 1.0)

pv(m, a) # ≈ 0.05410094201902403
```
