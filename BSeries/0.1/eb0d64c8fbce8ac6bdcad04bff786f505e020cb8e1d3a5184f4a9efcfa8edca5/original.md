```
bseries(rk::RungeKuttaMethod, order)
bseries(A::AbstractMatrix, b::AbstractVector, c::AbstractVector, order)
```

Compute the B-series of the Runge-Kutta method `rk` with Butcher coefficients `A, b, c` up to a prescribed integer `order`.

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by this method need to be multiplied by a power of the time step divided by the `symmetry` of the rooted tree and multiplied by the corresponding elementary differential of the input vector field $f$. See also [`evaluate`](@ref).

