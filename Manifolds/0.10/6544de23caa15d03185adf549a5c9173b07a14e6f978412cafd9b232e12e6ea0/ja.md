```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTangentVector},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTangentVector}
)
convert(
    ::Type{Tuple{T,T},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTangentVector}
) where {T<:AbstractVector}
```

点 [`PoincareHalfSpaceTangentVector`](@ref) `X`（$ℝ^n$ の）を `p` で、[`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のポアンカレ半平面モデルから [`HyperboloidPoint`](@ref) と [`HyperboloidTangentVector`](@ref) のタプル $π(p) ∈ ℝ^{n+1}$ に同時に変換します。

これは、ポアンカレボールモデルに変換し、そこからさらにハイパーボロイドに変換するという2つのステップで行われます。
