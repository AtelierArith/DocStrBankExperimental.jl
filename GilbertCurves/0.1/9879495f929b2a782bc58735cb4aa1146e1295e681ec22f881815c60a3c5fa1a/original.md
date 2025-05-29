```
gilbertindices(dims::Tuple{Int,Int}; majdim=dims[1] >= dims[2] ? 1 : 2)
```

Constructs a vector of `CartesianIndex` objects, orderd by a generalized Hilbert space-filling, starting at `CartesianIndex(1,1)`.  It will end at `CartesianIndex(dims[1],1)` if `majdim==1`, or `CartesianIndex(1,dims[2])` if `majdim==2` (or the closest feasible point).
