```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`HyperboloidPoint`](@ref) `p` と [`HyperboloidTVector`](@ref) `X` を同時に [`PoincareBallPoint`](@ref) と [`PoincareBallTVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareBallPoint}, ::HyperboloidPoint)`](@ref) と [`convert(::Type{PoincareBallTVector}, ::HyperboloidPoint, ::HyperboloidTVector)`](@ref) を参照してください。
