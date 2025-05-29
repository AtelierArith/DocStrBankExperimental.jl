```
MMEstimator{L1<:BoundedLossFunction, L2<:LossFunction} <: AbstractMEstimator
```

与えられた損失関数に対するMM推定量。

MM推定量は、二段階のプロセスを使用して得られます：

1. S推定量と損失関数 `L1` を使用して、高いブレークダウンポイントを持つロバストスケール推定を計算します。
2. 損失関数 `L2` を使用して、M推定量を用いて効率的な推定を計算します。

# フィールド

  * `loss1`: 高いブレークダウンポイントのS推定に使用される[`BoundedLossFunction`](@ref)。
  * `loss2`: 効率的なM推定に使用される[`LossFunction`](@ref)。
  * `scaleest`: S推定ステップでの推定かどうかを指定するブール値（`true`）またはM推定ステップ（`false`）。
