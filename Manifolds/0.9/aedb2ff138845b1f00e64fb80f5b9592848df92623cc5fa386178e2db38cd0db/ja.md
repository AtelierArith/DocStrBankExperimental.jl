```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTVector}}.
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTVector}
)
convert(
    ::Type{Tuple{P,T}},
    (p, X)::Tuple{PoincareBallPoint,PoincareBallTVector},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`PoincareBallPoint`](@ref) `p` と [`PoincareBallTVector`](@ref) `X` を同時に [`HyperboloidPoint`](@ref) と [`HyperboloidTVector`](@ref) に変換します。詳細は [`convert(::Type{HyperboloidPoint}, ::PoincareBallPoint)`](@ref) と [`convert(::Type{HyperboloidTVector}, ::PoincareBallPoint, ::PoincareBallTVector)`](@ref) を参照してください。
