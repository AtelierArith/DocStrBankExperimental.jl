```
GeneralizedQuantileEstimator{L<:LossFunction} <: AbstractQuantileEstimator
```

一般化分位数推定器は非対称損失関数を持つM推定器です。

[`L1Loss`](@ref)の場合、これは分位数回帰に対応します（ただし、分位数回帰には正確な解を提供する[`quantreg`](@ref)を使用する方が良いです）。

[`L2Loss`](@ref)の場合、これは期待値回帰に対応します（[`ExpectileEstimator`](@ref]を参照）。

# フィールド

  * `loss`: [`LossFunction`](@ref)。
  * `τ`: 推定する分位数値、0と1の間。

# プロパティ

  * `tau`、`q`、`quantile`は`τ`のエイリアスです。
