```
TDLearner(;approximator, method, γ=1.0, α=0.01, n=0)
```

時間差分法を使用して状態価値または状態-行動価値を推定します。

# フィールド

  * `approximator` は `<:TabularApproximator` です。
  * `γ=1.0` は割引率です。
  * `method`: 現在のところ `:SARS` (Q学習) のみがサポートされています。
  * `n=0`: 使用される時間ステップの数から 1 を引いた値です。
