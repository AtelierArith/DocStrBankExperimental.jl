```
bseries(avf::AverageVectorFieldMethod, order)
```

Compute the B-series of the [`AverageVectorFieldMethod`](@ref) up to a prescribed integer `order`.

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by `bseries` need to be multiplied by a power of the time step divided by the `symmetry` of the rooted tree and multiplied by the corresponding elementary differential of the input vector field $f$. See also [`evaluate`](@ref).

