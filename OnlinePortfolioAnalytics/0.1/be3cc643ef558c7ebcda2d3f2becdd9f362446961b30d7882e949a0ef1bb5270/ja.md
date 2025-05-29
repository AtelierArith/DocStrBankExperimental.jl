```julia
mutable struct DrawDowns{T} <: OnlinePortfolioAnalytics.AbstractDrawDowns{T}
```

```
DrawDowns{T}()
```

`DrawDowns`型はドローダウン計算（幾何学的方法）を実装しています。
