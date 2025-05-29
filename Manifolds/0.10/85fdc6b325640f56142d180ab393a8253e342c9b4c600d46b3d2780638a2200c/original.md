```
convert(::Type{PoincareHalfSpaceTangentVector}, p::HyperboloidPoint, ::HyperboloidTangentVector)
convert(::Type{PoincareHalfSpaceTangentVector}, p::P, X::T) where {P<:AbstractVector, T<:AbstractVector}
```

convert a [`HyperboloidTangentVector`](@ref) `X` at `p` to a [`PoincareHalfSpaceTangentVector`](@ref) on the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ by computing the push forward $π_*(p)[X]$ of the isometry $π$ that maps from the Hyperboloid to the Poincaré half space, cf. [`convert(::Type{PoincareHalfSpacePoint}, ::HyperboloidPoint)`](@ref).

This is done similarly to the approach there, i.e. by using the Poincaré ball model as an intermediate step.
