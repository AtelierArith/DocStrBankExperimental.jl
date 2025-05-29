```
SoftmaxRetraction <: AbstractRetractionMethod
```

Describes a retraction that is based on the softmax function.

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, SoftmaxRetraction())`, to implement a softmax retraction, define [`retract_softmax!`](@ref)`(M, q, p, X, t)` for your manifold `M`.

