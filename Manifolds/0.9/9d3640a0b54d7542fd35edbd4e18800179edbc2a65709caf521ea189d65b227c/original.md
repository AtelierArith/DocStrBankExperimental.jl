```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTVector}
)
```

Convert a [`PoincareBallPoint`](@ref) `p` and a [`PoincareBallTVector`](@ref) `X` to a [`PoincareHalfSpacePoint`](@ref) and a [`PoincareHalfSpaceTVector`](@ref) simultaneously, see [`convert(::Type{PoincareHalfSpacePoint}, ::PoincareBallPoint)`](@ref) and [`convert(::Type{PoincareHalfSpaceTVector}, ::PoincareBallPoint,::PoincareBallTVector)`](@ref) for the formulae.
