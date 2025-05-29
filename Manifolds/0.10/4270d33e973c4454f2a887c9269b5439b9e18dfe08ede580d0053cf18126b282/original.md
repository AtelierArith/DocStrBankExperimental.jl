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

Convert a [`PoincareBallPoint`](@ref) `p` and a [`PoincareBallTangentVector`](@ref) `X` to a [`HyperboloidPoint`](@ref) and a [`HyperboloidTangentVector`](@ref) simultaneously, see [`convert(::Type{HyperboloidPoint}, ::PoincareBallPoint)`](@ref) and [`convert(::Type{HyperboloidTangentVector}, ::PoincareBallPoint, ::PoincareBallTangentVector)`](@ref) for the formulae.
