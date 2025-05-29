```julia
struct SPOPlusLoss{F} <: InferOpt.AbstractLossLayer
```

スマート「予測-最適化」損失の凸代理。

# フィールド

  * `maximizer::Any`: 形式 `θ -> ŷ(θ) = argmax θᵀy` の線形最大化関数
  * `α::Float64`: 凸化パラメータ、デフォルト = 2.0

参考文献: [https://arxiv.org/abs/1710.08005](https://arxiv.org/abs/1710.08005)
