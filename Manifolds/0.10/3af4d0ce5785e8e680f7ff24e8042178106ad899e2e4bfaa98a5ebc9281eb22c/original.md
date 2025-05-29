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

Convert a [`HyperboloidPoint`](@ref) `p` and a [`HyperboloidTangentVector`](@ref) `X` to a [`PoincareBallPoint`](@ref) and a [`PoincareBallTangentVector`](@ref) simultaneously, see [`convert(::Type{PoincareBallPoint}, ::HyperboloidPoint)`](@ref) and [`convert(::Type{PoincareBallTangentVector}, ::HyperboloidPoint, ::HyperboloidTangentVector)`](@ref) for the formulae.
