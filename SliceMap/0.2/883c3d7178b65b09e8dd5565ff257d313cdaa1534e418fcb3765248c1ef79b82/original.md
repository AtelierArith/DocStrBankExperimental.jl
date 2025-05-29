```
MapCols{d}(f, m::Matrix, args...)
```

Similar to `mapcols(f, m, args...)`, but slices `m` into `SVector{d}` columns. Their length `d = size(M,1)` should ideally be provided for type-stability, but is not required.

The gradient for Tracker and Zygote uses `ForwardDiff` on each slice.
