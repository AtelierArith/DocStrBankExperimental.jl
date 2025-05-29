```
ProjectionInverseRetraction <: AbstractInverseRetractionMethod
```

Inverse retractions that are based on a projection (or its inversion).

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, ProjectionInverseRetraction())`, to implement an inverse projection retraction, define [`inverse_retract_project!`](@ref)`(M, X, p, q)` for your manifold `M`.

