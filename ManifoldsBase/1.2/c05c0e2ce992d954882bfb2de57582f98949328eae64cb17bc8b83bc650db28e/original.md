```
PolarInverseRetraction <: AbstractInverseRetractionMethod
```

Inverse retractions that are based on a singular value decomposition of the matrix / matrices for point and tangent vector on a [`AbstractManifold`](@ref)

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, PolarInverseRetraction())`, to implement an inverse polar retraction, define [`inverse_retract_polar!`](@ref)`(M, X, p, q)` for your manifold `M`.

