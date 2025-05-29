```
AbstractRegularized <: AbstractOptimizationLayer
```

ブラックボックス線形（θにおいて）最適化手法の凸正則化摂動

```
ŷ(θ) = argmax_{y ∈ C} {θᵀg(y) + h(y) - Ω(y)}
```

ここで、gとhはyの関数です。

# インターフェース

  * `(regularized::AbstractRegularized)(θ; kwargs...)`: `ŷ(θ)`を返す
  * `compute_regularization(regularized, y)`: `Ω(y)`を返す
  * `get_maximizer(regularized)`: 関連する最適化手法を返す

# 利用可能な実装

  * [`SoftArgmax`](@ref)
  * [`SparseArgmax`](@ref)
  * [`SoftRank`](@ref)
  * [`RegularizedFrankWolfe`](@ref)
