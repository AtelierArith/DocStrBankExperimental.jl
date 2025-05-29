```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTangentVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p, X)::Tuple{T,T},
) where {T <: AbstractVector}
```

Convert a [`PoincareHalfSpacePoint`](@ref) `p` and a [`PoincareHalfSpaceTangentVector`](@ref) `X` to a [`PoincareBallPoint`](@ref) and a [`PoincareBallTangentVector`](@ref) simultaneously, see [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref) and [`convert(::Type{PoincareBallTangentVector}, ::PoincareHalfSpacePoint, ::PoincareHalfSpaceTangentVector)`](@ref) for the formulae.
