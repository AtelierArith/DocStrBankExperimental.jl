```
distance(M::AbstractPowerManifold, p, q, r::Real=2)
distance(M::AbstractPowerManifold, p, q, m::AbstractInverseRetractionMethod=LogarithmicInverseRetraction(), r::Real=2)
```

Compute the distance between `q` and `p` on an [`AbstractPowerManifold`](@ref).

First, the componentwise distances are computed using the Riemannian distance function on `M.manifold`. These can be approximated using the `norm` of an [`AbstractInverseRetractionMethod`](@ref) `m`. This yields an array of distance values.

Second, we compute the `r`-norm on this array of distances. This is also the only place, there the `r` is used.
