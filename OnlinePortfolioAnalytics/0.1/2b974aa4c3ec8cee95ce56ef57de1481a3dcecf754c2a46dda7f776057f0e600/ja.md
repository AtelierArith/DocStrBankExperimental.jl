```julia
mutable struct Sharpe{T} <: OnlinePortfolioAnalytics.PortfolioAnalyticsSingleOutput{T}
```

```
Sharpe{T}(; period=252, risk_free=0)
```

`Sharpe`型はシャープレシオの計算を実装しています。

# パラメータ

  * `period`: デフォルトは `252`。日次（`252`）、時間単位（`252*6.5`）、分単位（`252*6.5*60`）など...
  * `risk_free`: デフォルトは `0`。期間中の一定のリスクフリーリターン。
