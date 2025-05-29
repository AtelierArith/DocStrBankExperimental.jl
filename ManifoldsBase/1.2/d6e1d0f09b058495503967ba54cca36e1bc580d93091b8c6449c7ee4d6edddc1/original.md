```
CayleyRetraction <: AbstractRetractionMethod
```

A retraction based on the Cayley transform, which is realized by using the [`PadeRetraction`](@ref)`{1}`.

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, CayleyRetraction())`, to implement a caley retraction, define [`retract_cayley!`](@ref)`(M, q, p, X, t)` for your manifold `M`. By default both these functions fall back to calling a [`PadeRetraction`](@ref)`(1)`.

