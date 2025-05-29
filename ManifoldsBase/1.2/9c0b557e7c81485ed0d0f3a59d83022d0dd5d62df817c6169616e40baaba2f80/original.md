```
inverse_retract(M::ProductManifold, p, q, m::AbstractInverseRetractionMethod)
```

Compute the inverse retraction from `p` with respect to `q` on the [`ProductManifold`](@ref) `M` using an [`AbstractInverseRetractionMethod`](@ref), which is used on each manifold of the product.
