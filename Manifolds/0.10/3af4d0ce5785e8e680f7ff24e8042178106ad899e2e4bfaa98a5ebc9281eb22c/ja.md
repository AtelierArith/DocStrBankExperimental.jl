```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTangentVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

[`HyperboloidPoint`](@ref) `p` と [`HyperboloidTangentVector`](@ref) `X` を同時に [`PoincareBallPoint`](@ref) と [`PoincareBallTangentVector`](@ref) に変換します。式については [`convert(::Type{PoincareBallPoint}, ::HyperboloidPoint)`](@ref) と [`convert(::Type{PoincareBallTangentVector}, ::HyperboloidPoint, ::HyperboloidTangentVector)`](@ref) を参照してください。
