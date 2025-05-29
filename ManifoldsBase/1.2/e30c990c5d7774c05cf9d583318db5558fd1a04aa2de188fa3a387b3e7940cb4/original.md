```
PadeInverseRetraction{m} <: AbstractInverseRetractionMethod
```

An inverse retraction based on the Padé approximation of order $m$ for the retraction.

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, PadeInverseRetraction(m))`, to implement an inverse Padé retraction, define [`inverse_retract_pade!`](@ref)`(M, X, p, q, m)` for your manifold `M`.

