```
PositionBasis(xmin, xmax, Npoints)
PositionBasis(b::MomentumBasis)
```

Basis for a particle in real space.

For simplicity periodic boundaries are assumed which means that the rightmost point defined by `xmax` is not included in the basis but is defined to be the same as `xmin`.

When a [`MomentumBasis`](@ref) is given as argument the exact values of $x_{min}$ and $x_{max}$ are due to the periodic boundary conditions more or less arbitrary and are chosen to be $-\pi/dp$ and $\pi/dp$ with $dp=(p_{max}-p_{min})/N$.
