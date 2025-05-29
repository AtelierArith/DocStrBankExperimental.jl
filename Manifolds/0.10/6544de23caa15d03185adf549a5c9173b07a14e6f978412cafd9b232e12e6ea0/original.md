```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTangentVector},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTangentVector}
)
convert(
    ::Type{Tuple{T,T},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTangentVector}
) where {T<:AbstractVector}
```

convert a point [`PoincareHalfSpaceTangentVector`](@ref) `X` (from $ℝ^n$) at `p` from the Poincaré half plane model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a tuple of a [`HyperboloidPoint`](@ref) and a [`HyperboloidTangentVector`](@ref) $π(p) ∈ ℝ^{n+1}$ simultaneously.

This is done in two steps, namely transforming it to the Poincare ball model and from there further on to a Hyperboloid.
