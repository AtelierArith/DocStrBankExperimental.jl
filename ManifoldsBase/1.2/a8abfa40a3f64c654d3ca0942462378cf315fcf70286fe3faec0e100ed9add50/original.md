```
inverse_retract(M::AbstractPowerManifold, p, q, m::AbstractInverseRetractionMethod)
```

Compute the inverse retraction from `p` with respect to `q` on an [`AbstractPowerManifold`](@ref) `M` using an [`AbstractInverseRetractionMethod`](@ref). Then this method is performed elementwise, so the inverse retraction method has to be one that is available on the base [`AbstractManifold`](@ref).
