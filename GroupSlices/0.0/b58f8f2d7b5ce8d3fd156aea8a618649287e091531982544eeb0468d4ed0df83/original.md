```
groupinds(ic)
```

Returns a vector of vectors of integers wherein the vector of group slice index integers as returned from `groupslices(A, dim)` is converted into a grouped vector of vectors.  Each vector entry in the returned vector of vectors contains all of the positional indices of slices in the original input array `A` that correspond to the unique slices along dimension `dim` that are present in the array `C` as returned from `unique(A, dim)`.
