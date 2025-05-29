```
SoftRank{is_l2_regularized} <: AbstractRegularized
```

高速な微分可能なランキング正則化層です。`is_l2_regularized`がtrueの場合はL2正則化を使用し、そうでない場合はエントロピー（kl）正則化を使用します。

[`AbstractRegularized`](@ref)層として、[`FenchelYoungLoss`](@ref)を用いた教師あり学習にも使用できます。

# フィールド

  * `ε::Float64`: 正則化のサイズ
  * `rev::Bool`: falseの場合は昇順でランク付け

参考文献: [https://arxiv.org/abs/2002.08871](https://arxiv.org/abs/2002.08871)
