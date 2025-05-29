```
PredictionStateSpace{T, ST <: AbstractStateSpace{T}, KT, QT, RT, ST2} <: AbstractPredictionStateSpace{T}
PredictionStateSpace(sys, K, Q=nothing, R=nothing, S=nothing)
```

予測目的のための追加のカルマンフィルターモデルを含む状態空間型です。

# 引数:

  * `sys`: 説明
  * `K`: 無限ホライズンカルマンゲイン
  * `Q = nothing`: 動力学の共分散
  * `R = nothing`: 測定の共分散
  * `S = nothing`: クロス共分散
