```
retract(M::AbstractPowerManifold, p, X, method::AbstractRetractionMethod)
```

Compute the retraction from `p` with tangent vector `X` on an [`AbstractPowerManifold`](@ref) `M` using a [`AbstractRetractionMethod`](@ref). Then this method is performed elementwise, so the retraction method has to be one that is available on the base [`AbstractManifold`](@ref).
