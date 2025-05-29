```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTangentVector}
)
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p, X)::Tuple{P,T},
) where {P<:AbstractVector, T <: AbstractVector}
```

Convert a [`HyperboloidPoint`](@ref) `p` and a [`HyperboloidTangentVector`](@ref) `X` to a [`PoincareHalfSpacePoint`](@ref) and a [`PoincareHalfSpaceTangentVector`](@ref) simultaneously, see [`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref) and [`convert(::Type{PoincareHalfSpaceTangentVector}, ::Tuple{HyperboloidPoint,HyperboloidTangentVector})`](@ref) for the formulae.
