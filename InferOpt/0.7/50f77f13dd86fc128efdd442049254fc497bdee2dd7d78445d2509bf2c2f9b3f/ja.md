```julia
struct FenchelYoungLoss{O<:InferOpt.AbstractOptimizationLayer} <: InferOpt.AbstractLossLayer
```

与えられた最適化層に関連するフェンケル-ヤング損失。

```
L(θ, y_true) = (Ω(y_true) - θᵀy_true) - (Ω(ŷ) - θᵀŷ)
```

参考文献: [https://arxiv.org/abs/1901.02324](https://arxiv.org/abs/1901.02324)

# フィールド

  * `optimization_layer::AbstractOptimizationLayer`: `ŷ(θ) = argmax {θᵀy - Ω(y)}`（正則化または摂動されたもの）として定式化できる最適化層

# 互換性

この損失は以下と互換性があります：

  * [`LinearMaximizer`](@ref)ベースの層。
  * 加法的または乗法的摂動を持つ[`PerturbedOracle`](@ref)層（一般的な摂動はサポートされていません）。
  * 任意の[`AbstractRegularized`](@ref)層。
