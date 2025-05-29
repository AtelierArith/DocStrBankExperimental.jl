```
lc_analytic(::CrawfordMethod, InitialEffort, TotalUnits, Learning)
```

Compute the cumulative cost using Crawford's learning curve model.

Formula:     cost = Σ(i=1 to TotalUnits)[ InitialEffort * i ^ (log(Learning) / log(2)) ]
