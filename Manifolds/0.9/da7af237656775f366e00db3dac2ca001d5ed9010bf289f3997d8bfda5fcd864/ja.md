```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTVector}
)
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`HyperboloidPoint`](@ref) `p` と [`HyperboloidTVector`](@ref) `X` を同時に [`PoincareHalfSpacePoint`](@ref) と [`PoincareHalfSpaceTVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref) と [`convert(::Type{PoincareHalfSpaceTVector}, ::Tuple{HyperboloidPoint,HyperboloidTVector})`](@ref) を参照してください。
