```
addgrid!(sim, lsize; distance, align, jitter, kwargs...)
```

Add particles on a `D`-dimensional Cartesian lattice.

The lattice extends for `lsize[i]` particles in the `i`th dimension, with a distance of `distance[i]` in between particle `centerpos`s. If `lsize[i]` is smaller than 1, the amount of cells will be chosen so that the lattice fills the entire domain along the `i`th dimension, with a margin of `distance[i]/2`.

Grid points are jittered by adding random numbers drawn from the interval `[-jitter[i]/2, jitter[i]/2]`.

`align` specifies the position of the grid in the domain. If `align[i]` is a number, the `i`th coordinate of the grid centroid will be placed at `align[i]`. If `align[i]` is either `:center`, `:centre`, `:start` or `end`, the grid will be aligned with the center, start or end of the domain along the `i`th coordinate.

All lattice parameters (`lsize`, `distance`, `align`, `jitter`) can be specified either as a `D`-vector or as a scalar. In the latter case, they are interpreted as isotropic.
