```
compute_cost(model, X, Y, with_gradients=false)
```

モデルの予測と真の値に基づいてコスト関数 (C) を計算します。

...

# 引数

  * `model::ApplicationDrivenLearning.Model`: 評価するモデル。
  * `X::Matrix{<:Real}`: 入力データ。
  * `Y::Matrix{<:Real}`: 真の値。
  * `with_gradients::Bool=false`: 勾配を計算して返すフラグ。...
