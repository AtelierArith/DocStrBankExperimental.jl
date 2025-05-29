```
SoftmaxInverseRetraction <: AbstractInverseRetractionMethod
```

Describes an inverse retraction that is based on the softmax function.

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, SoftmaxInverseRetraction())`, to implement an inverse softmax retraction, define [`inverse_retract_softmax!`](@ref)`(M, X, p, q)` for your manifold `M`.

