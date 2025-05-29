```
lc_analytic(::WrightMethod, InitialEffort, TotalUnits, Learning)
```

Compute the cumulative cost using Wright's learning curve model.

Formula:     cost = InitialEffort * (TotalUnits ^ ((log(Learning) / log(2)) + 1))
