```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTangentVector}
)
```

Convert a [`PoincareBallPoint`](@ref) `p` and a [`PoincareBallTangentVector`](@ref) `X` to a [`PoincareHalfSpacePoint`](@ref) and a [`PoincareHalfSpaceTangentVector`](@ref) simultaneously, see [`convert(::Type{PoincareHalfSpacePoint}, ::PoincareBallPoint)`](@ref) and [`convert(::Type{PoincareHalfSpaceTangentVector}, ::PoincareBallPoint,::PoincareBallTangentVector)`](@ref) for the formulae.
