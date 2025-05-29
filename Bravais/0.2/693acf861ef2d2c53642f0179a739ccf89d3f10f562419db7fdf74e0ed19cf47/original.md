```
Bravais.DirectBasis{D, E} <: AbstractBasis{D, E}
```

A wrapper type over `D` distinct `D`-dimensional vectors (given as a `SVector{D, SVector{D, E}}`), defining a lattice basis in direct space. By default (i.e., if omitted), `E` is `Float64`.
