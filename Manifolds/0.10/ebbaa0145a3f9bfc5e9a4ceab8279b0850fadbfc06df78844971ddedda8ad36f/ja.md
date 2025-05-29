```
convert(::Type{HyperboloidTangentVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTangentVector)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTangentVector)
```

点 [`PoincareHalfSpaceTangentVector`](@ref) `X`（$ℝ^n$ の）を、Poincaré 半平面モデルの [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ における点 `p` から [`HyperboloidTangentVector`](@ref) $π(p) ∈ ℝ^{n+1}$ に変換します。

これは二つのステップで行われ、まず Poincare ボールの点に変換し、そこからさらに Hyperboloid の点に進みます。
