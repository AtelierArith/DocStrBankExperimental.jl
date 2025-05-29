```
TauEstimator{L1<:BoundedLossFunction, L2<:BoundedLossFunction} <: AbstractMEstimator
```

与えられた損失関数に対するτ推定量。

τ推定量はM推定に対応しており、損失関数は高いブレークダウンポイントの損失と効率的な損失の加重和です。重みは反復的に再重み付けされた最小二乗法の各ステップで再計算されるため、推定値は堅牢（高いブレークダウンポイント）であり、効率的です。

# フィールド

  * `loss1`: 高いブレークダウンポイントの [`BoundedLossFunction`](@ref)。
  * `loss2`: 高い効率の [`BoundedLossFunction`](@ref)。
  * `w`: 損失の和における重み: `w . loss1 + loss2`。
