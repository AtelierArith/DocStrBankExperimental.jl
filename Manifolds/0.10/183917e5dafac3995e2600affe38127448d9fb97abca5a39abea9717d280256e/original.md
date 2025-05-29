```
convert(::Type{HyperboloidPoint}, p::PoincareHalfSpacePoint)
convert(::Type{AbstractVector}, p::PoincareHalfSpacePoint)
```

convert a point [`PoincareHalfSpacePoint`](@ref) `p` (from $ℝ^n$) from the Poincaré half plane model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`HyperboloidPoint`](@ref) $π(p) ∈ ℝ^{n+1}$.

This is done in two steps, namely transforming it to a Poincare ball point and from there further on to a Hyperboloid point.
