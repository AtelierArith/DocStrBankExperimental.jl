```
FastVector{T} <: AbstractVector{T}
```

A vector with preallocated memory than can only increase in size. Compared to normal vector, this improves the performance of mesh generation by about 50%. If this is already implemented somewhere, please let me know.
