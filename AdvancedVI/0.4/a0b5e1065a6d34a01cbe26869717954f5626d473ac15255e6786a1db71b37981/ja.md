```
StickingTheLandingEntropy()
```

「着地を決める」エントロピー推定器[^RWD2017]。

# 要件

  * 変分近似 `q` は `logpdf` を実装します。
  * `logpdf(q, η)` は選択したADフレームワークによって微分可能でなければなりません。
