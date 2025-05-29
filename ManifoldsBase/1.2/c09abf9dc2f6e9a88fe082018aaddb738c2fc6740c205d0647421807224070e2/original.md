```
CayleyInverseRetraction <: AbstractInverseRetractionMethod
```

A retraction based on the Cayley transform, which is realized by using the [`PadeRetraction`](@ref)`{1}`.

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, CayleyInverseRetraction())`, to implement an inverse caley retraction, define [`inverse_retract_cayley!`](@ref)`(M, X, p, q)` for your manifold `M`. By default both these functions fall back to calling a [`PadeInverseRetraction`](@ref)`(1)`.

