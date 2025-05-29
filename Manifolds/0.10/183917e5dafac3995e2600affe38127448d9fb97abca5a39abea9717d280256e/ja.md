```
convert(::Type{HyperboloidPoint}, p::PoincareHalfSpacePoint)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint)
```

点 [`PoincareHalfSpacePoint`](@ref) `p` を Poincaré 半平面モデルから [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ への変換を行い、[`HyperboloidPoint`](@ref) $π(p) ∈ ℝ^{n+1}$ に変換します。

これは二つのステップで行われ、まず Poincare ボール点に変換し、そこからさらに Hyperboloid 点に変換します。
