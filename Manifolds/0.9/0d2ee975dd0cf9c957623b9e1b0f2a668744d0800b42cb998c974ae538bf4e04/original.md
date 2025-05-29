```
convert(
    ::Type{Tuple{HyperboloidPoint,HyperboloidTVector},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTVector}
)
convert(
    ::Type{Tuple{T,T},
    (p,X)::Tuple{PoincareHalfSpacePoint, PoincareHalfSpaceTVector}
) where {T<:AbstractVector}
```

convert a point [`PoincareHalfSpaceTVector`](@ref) `X` (from $ℝ^n$) at `p` from the Poincaré half plane model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a tuple of a [`HyperboloidPoint`](@ref) and a [`HyperboloidTVector`](@ref) $π(p) ∈ ℝ^{n+1}$ simultaneously.

This is done in two steps, namely transforming it to the Poincare ball model and from there further on to a Hyperboloid.
