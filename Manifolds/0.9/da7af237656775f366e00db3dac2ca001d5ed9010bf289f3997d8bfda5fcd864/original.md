```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTVector}
)
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

Convert a [`HyperboloidPoint`](@ref) `p` and a [`HyperboloidTVector`](@ref) `X` to a [`PoincareHalfSpacePoint`](@ref) and a [`PoincareHalfSpaceTVector`](@ref) simultaneously, see [`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref) and [`convert(::Type{PoincareHalfSpaceTVector}, ::Tuple{HyperboloidPoint,HyperboloidTVector})`](@ref) for the formulae.
