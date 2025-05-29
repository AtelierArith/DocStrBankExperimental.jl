```
convert(::Type{PoincareHalfSpacePoint}, p::Hyperboloid)
convert(::Type{PoincareHalfSpacePoint}, p)
```

convert a [`HyperboloidPoint`](@ref) or `Vector``p` (from $ℝ^{n+1}$) from the Hyperboloid model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`PoincareHalfSpacePoint`](@ref) $π(x) ∈ ℝ^{n}$.

This is done in two steps, namely transforming it to a Poincare ball point and from there further on to a PoincareHalfSpacePoint point.
