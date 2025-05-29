```
ProjectionRetraction <: AbstractRetractionMethod
```

Retractions that are based on projection and usually addition in the embedding.

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, ProjectionRetraction())`, to implement a projection retraction, define [`retract_project!`](@ref)`(M, q, p, X, t)` for your manifold `M`.

