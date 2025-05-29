```
bseries(ark::AdditiveRungeKuttaMethod, order)
```

Compute the B-series of the additive Runge-Kutta method `ark` up to a prescribed integer `order`.

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by this method need to be multiplied by a power of the time step divided by the `symmetry` of the colored rooted tree and multiplied by the corresponding elementary differential of the input vector fields $f^\nu$. See also [`evaluate`](@ref).

