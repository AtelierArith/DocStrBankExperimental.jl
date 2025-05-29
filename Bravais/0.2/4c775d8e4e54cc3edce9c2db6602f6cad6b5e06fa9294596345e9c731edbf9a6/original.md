```
Bravais.ReciprocalBasis{D, E} <: AbstractBasis{D, E}
```

A wrapper type over `D` distinct `D`-dimensional vectors (given as a `SVector{D, SVector{D, E}}`), defining a lattice basis in reciprocal space. By default (i.e., if omitted), `E` is `Float64`.
