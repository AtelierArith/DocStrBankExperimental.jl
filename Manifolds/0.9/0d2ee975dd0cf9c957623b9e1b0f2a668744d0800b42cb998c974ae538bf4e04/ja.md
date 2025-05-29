```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTVector},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTVector}
)
convert(
    ::Type{Tuple{T,T},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTVector}
) where {T<:AbstractVector}
```

点 [`PoincareHalfSpaceTVector`](@ref) `X` を $ℝ^n$ で `p` から、[`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のポアンカレ半平面モデルから、[`HyperboloidPoint`](@ref) と [`HyperboloidTVector`](@ref) のタプル $π(p) ∈ ℝ^{n+1}$ に同時に変換します。

これは二段階で行われ、まずポアンカレボールモデルに変換し、そこからさらにハイパーボロイドに進みます。
