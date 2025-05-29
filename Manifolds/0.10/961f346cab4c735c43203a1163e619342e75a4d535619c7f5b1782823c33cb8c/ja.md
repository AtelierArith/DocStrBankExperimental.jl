```
convert(::Type{PoincareHalfSpacePoint}, p::Hyperboloid)
convert(::Type{PoincareHalfSpacePoint}, p)
```

[`HyperboloidPoint`](@ref) または `Vector``p` (from $ℝ^{n+1}$) を、[`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のハイパーボロイドモデルから [`PoincareHalfSpacePoint`](@ref) $π(x) ∈ ℝ^{n}$ に変換します。

これは二段階で行われ、まずポアンカレボール点に変換し、そこからさらにポアンカレ半空間点に変換します。
