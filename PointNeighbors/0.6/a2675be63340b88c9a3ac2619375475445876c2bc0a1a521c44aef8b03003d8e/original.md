```
DictionaryCellList{NDIMS}()
```

A simple cell list implementation where a cell index `(i, j)` or `(i, j, k)` is mapped to a `Vector{Int}` by a `Dict`. By using a dictionary, which only stores non-empty cells, the domain is potentially infinite.

This implementation is very simple, but it neither uses an optimized hash function for integer tuples, nor does it use a contiguous memory layout. Consequently, this cell list is not GPU-compatible.

# Arguments

  * `NDIMS`: Number of dimensions.
