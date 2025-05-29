```
Grid(dims::AbstractVector, G=Graph; periodic=false)
```

Creates a `d`-dimensional cubic lattice, with `d=length(dims)` and length  `dims[i]` in dimension `i`. If `periodic=true` the resulting lattice will have periodic boundary condition in each dimension.
