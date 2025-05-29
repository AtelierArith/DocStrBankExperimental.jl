```
PolarRetraction <: AbstractRetractionMethod
```

Retractions that are based on singular value decompositions of the matrix / matrices for point and tangent vectors.

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, PolarRetraction())`, to implement a polar retraction, define [`retract_polar!`](@ref)`(M, q, p, X, t)` for your manifold `M`.

