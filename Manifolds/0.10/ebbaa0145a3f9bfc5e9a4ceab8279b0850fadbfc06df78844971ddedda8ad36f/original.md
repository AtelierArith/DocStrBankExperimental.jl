```
convert(::Type{HyperboloidTangentVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTangentVector)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint, X::PoincareHalfSpaceTangentVector)
```

convert a point [`PoincareHalfSpaceTangentVector`](@ref) `X` (from $ℝ^n$) at `p` from the Poincaré half plane model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`HyperboloidTangentVector`](@ref) $π(p) ∈ ℝ^{n+1}$.

This is done in two steps, namely transforming it to a Poincare ball point and from there further on to a Hyperboloid point.
