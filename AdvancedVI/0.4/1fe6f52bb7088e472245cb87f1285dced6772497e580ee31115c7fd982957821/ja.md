```
MonteCarloEntropy()
```

エントロピーのモンテカルロ推定。

# 要件

  * 変分近似 `q` は `logpdf` を実装しています。
  * `logpdf(q, η)` は選択したADフレームワークによって微分可能でなければなりません。
