```
org = origin(A)
```

yields the index at origin of coordinates in the Cartesian mesh or array `A`. The origin is defined as the index where all coordinates of the nodes are zero. The returned value may be `nothing` if the origin is at index `(0,0,...)`, a single array index if the origin is at the same index for all dimensions, or a tuple of array indices. Indices may be integers and/or reals for fractional indices.

Call `origin(Tuple, A)` to retrieve a `N`-dimensional (possibly fractional) index in all cases.
