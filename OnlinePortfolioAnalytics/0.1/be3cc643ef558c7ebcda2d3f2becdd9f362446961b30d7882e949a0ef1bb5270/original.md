```julia
mutable struct DrawDowns{T} <: OnlinePortfolioAnalytics.AbstractDrawDowns{T}
```

```
DrawDowns{T}()
```

The `DrawDowns` type implements drawdowns calculations (geometric method).
