```
distance(M::ProductManifold, p, q, r::Real=2)
distance(M::ProductManifold, p, q, m::AbstractInverseRetractionMethod=LogarithmicInverseRetraction(), r::Real=2)
```

Compute the distance between `q` and `p` on an [`ProductManifold`](@ref).

First, the componentwise distances are computed. These can be approximated using the `norm` of an [`AbstractInverseRetractionMethod`](@ref) `m`. Then, the `r`-norm of the tuple of these elements is computed.
