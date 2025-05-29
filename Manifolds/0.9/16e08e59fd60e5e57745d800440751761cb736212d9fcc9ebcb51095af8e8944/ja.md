```
convert(::Type{HyperboloidTVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTVector)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTVector)
```

点 [`PoincareHalfSpaceTVector`](@ref) `X`（$ℝ^n$ の）を `p` から Poincaré 半平面モデルの [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ へ変換し、[`HyperboloidTVector`](@ref) $π(p) ∈ ℝ^{n+1}$ にします。

これは二つのステップで行われ、まず Poincare ボール点に変換し、そこからさらに Hyperboloid 点に進みます。
