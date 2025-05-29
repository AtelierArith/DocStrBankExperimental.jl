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

Convert a [`PoincareBallPoint`](@ref) `p` and a [`PoincareBallTVector`](@ref) `X` to a [`HyperboloidPoint`](@ref) and a [`HyperboloidTVector`](@ref) simultaneously, see [`convert(::Type{HyperboloidPoint}, ::PoincareBallPoint)`](@ref) and [`convert(::Type{HyperboloidTVector}, ::PoincareBallPoint, ::PoincareBallTVector)`](@ref) for the formulae.
