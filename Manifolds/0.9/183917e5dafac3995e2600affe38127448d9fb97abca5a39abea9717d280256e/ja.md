```
convert(::Type{HyperboloidPoint}, p::PoincareHalfSpacePoint)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint)
```

点 [`PoincareHalfSpacePoint`](@ref) `p` を Poincaré 半平面モデルの [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ から [`HyperboloidPoint`](@ref) $π(p) ∈ ℝ^{n+1}$ に変換します。

これは二段階で行われ、まず Poincare ボール点に変換し、そこからさらに Hyperboloid 点に進みます。
