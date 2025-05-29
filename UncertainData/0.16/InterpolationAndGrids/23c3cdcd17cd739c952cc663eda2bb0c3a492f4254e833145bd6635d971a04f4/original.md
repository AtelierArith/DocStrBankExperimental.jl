```
bin!(bins::Vector{AbstractVector{T}}, left_bin_edges::AbstractRange{T}, xs, ys) where T
```

Distribute the elements of `ys` into `N-1` different pre-allocated empty  bin vectors, based on how the values in `xs` are distributed among  the bins defined by the `N` grid points in `left_bin_edges`. `bins` must be a vector of vector-like mutable containers.

If `xs[i]` falls in the `n`-th bin interval, then `ys[i]`  is assigned to the `n`-th bin vector. If `xs[i]` lie outside the grid,  the corresponding `ys[i]` is ignored.

See also [`bin(::AbstractRange)`](@ref).
