```
MomentumBasis(pmin, pmax, Npoints)
MomentumBasis(b::PositionBasis)
```

Basis for a particle in momentum space.

For simplicity periodic boundaries are assumed which means that `pmax` is not included in the basis but is defined to be the same as `pmin`.

When a [`PositionBasis`](@ref) is given as argument the exact values of $p_{min}$ and $p_{max}$ are due to the periodic boundary conditions more or less arbitrary and are chosen to be $-\pi/dx$ and $\pi/dx$ with $dx=(x_{max}-x_{min})/N$.
