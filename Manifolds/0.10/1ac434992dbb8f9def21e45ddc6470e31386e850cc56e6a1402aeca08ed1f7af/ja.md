```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTangentVector}
)
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`HyperboloidPoint`](@ref) `p` と [`HyperboloidTangentVector`](@ref) `X` を同時に [`PoincareHalfSpacePoint`](@ref) と [`PoincareHalfSpaceTangentVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref) と [`convert(::Type{PoincareHalfSpaceTangentVector}, ::Tuple{HyperboloidPoint,HyperboloidTangentVector})`](@ref) を参照してください。
