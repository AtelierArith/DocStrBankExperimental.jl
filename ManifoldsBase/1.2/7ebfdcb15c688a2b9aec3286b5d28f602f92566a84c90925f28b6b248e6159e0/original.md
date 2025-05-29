```
inverse_retract(M::ProductManifold, p, q, m::InverseProductRetraction)
```

Compute the inverse retraction from `p` with respect to `q` on the [`ProductManifold`](@ref) `M` using an [`InverseProductRetraction`](@ref), which by default encapsulates a inverse retraction for each manifold of the product. Then this method is performed elementwise, so the encapsulated inverse retraction methods have to be available per factor.
