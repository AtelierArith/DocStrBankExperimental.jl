```
retract(M::ProductManifold, p, X, m::ProductRetraction)
```

Compute the retraction from `p` with tangent vector `X` on the [`ProductManifold`](@ref) `M` using an [`ProductRetraction`](@ref), which by default encapsulates retractions of the base manifolds. Then this method is performed elementwise, so the encapsulated retractions method has to be one that is available on the manifolds.
