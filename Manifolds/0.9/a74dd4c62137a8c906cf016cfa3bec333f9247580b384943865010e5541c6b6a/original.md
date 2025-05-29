```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p, X)::Tuple{T,T},
) where {T <: AbstractVector}
```

Convert a [`PoincareHalfSpacePoint`](@ref) `p` and a [`PoincareHalfSpaceTVector`](@ref) `X` to a [`PoincareBallPoint`](@ref) and a [`PoincareBallTVector`](@ref) simultaneously, see [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref) and [`convert(::Type{PoincareBallTVector}, ::PoincareHalfSpacePoint, ::PoincareHalfSpaceTVector)`](@ref) for the formulae.
