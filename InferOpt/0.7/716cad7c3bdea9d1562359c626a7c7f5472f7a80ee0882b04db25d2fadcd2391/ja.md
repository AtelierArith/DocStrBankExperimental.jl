```
SoftSort{is_l2_regularized} <: AbstractOptimizationLayer
```

高速な微分可能なソート最適化レイヤーです。`is_l2_regularized`がtrueの場合はL2正則化を使用し、そうでない場合はエントロピー（kl）正則化を使用します。

参照 [https://arxiv.org/abs/2002.08871](https://arxiv.org/abs/2002.08871)

# フィールド

  * `ε::Float64`: 正則化のサイズ
  * `rev::Bool`: falseの場合は昇順にソート
