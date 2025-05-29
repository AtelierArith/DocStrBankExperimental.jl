```julia
mutable struct ArithmeticDrawDowns{T} <: OnlinePortfolioAnalytics.AbstractDrawDowns{T}
```

```
ArithmeticDrawDowns{T}()
```

The `ArithmeticDrawDowns` type implements drawdowns calculations (arithmetic method).
