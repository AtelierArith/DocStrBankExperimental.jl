```
PadeRetraction{m} <: AbstractRetractionMethod
```

A retraction based on the Padé approximation of order $m$

# Constructor

```
PadeRetraction(m::Int)
```

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, PadeRetraction(m))`, to implement a Padé retraction, define [`retract_pade!`](@ref)`(M, q, p, X, t, m)` for your manifold `M`.

