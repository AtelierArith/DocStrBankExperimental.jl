```julia
mutable struct ArithmeticDrawDowns{T} <: OnlinePortfolioAnalytics.AbstractDrawDowns{T}
```

```
ArithmeticDrawDowns{T}()
```

`ArithmeticDrawDowns`型はドローダウン計算（算術法）を実装しています。
