```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTangentVector}}.
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTangentVector}
)
convert(
    ::Type{Tuple{P,T}},
    (p, X)::Tuple{PoincareBallPoint,PoincareBallTangentVector},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`PoincareBallPoint`](@ref) `p` と [`PoincareBallTangentVector`](@ref) `X` を同時に [`HyperboloidPoint`](@ref) と [`HyperboloidTangentVector`](@ref) に変換します。詳細は [`convert(::Type{HyperboloidPoint}, ::PoincareBallPoint)`](@ref) と [`convert(::Type{HyperboloidTangentVector}, ::PoincareBallPoint, ::PoincareBallTangentVector)`](@ref) を参照してください。
