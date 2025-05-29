```
StickingTheLandingEntropyZeroGradient()
```

「着地を決める」エントロピー推定器[^RWD2017]ですが、平均ゼロの勾配を持つように修正されています。これは、`ProximalLocationScaleEntropy`とのみ使用されることが期待されています。

# 要件

  * 変分近似 `q` は `logpdf` を実装しています。
  * `logpdf(q, η)` は選択したADフレームワークによって微分可能でなければなりません。
  * 変分近似は `entropy` を実装しています。
