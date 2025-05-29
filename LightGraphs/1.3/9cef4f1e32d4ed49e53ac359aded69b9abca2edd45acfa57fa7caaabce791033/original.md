```
gdistances!(g, source, dists; sort_alg=QuickSort)
```

Fill `dists` with the geodesic distances of vertices in `g` from source vertex (or collection of vertices) `source`. `dists` should be a vector of length `nv(g)`  filled with `typemax(T)`. Return `dists`.

For vertices in disconnected components the default distance is `typemax(T)`.

An optional sorting algorithm may be specified (see Performance section).

### Performance

`gdistances` uses `QuickSort` internally for its default sorting algorithm, since it performs the best of the algorithms built into Julia Base. However, passing a `RadixSort` (available via [SortingAlgorithms.jl](https://github.com/JuliaCollections/SortingAlgorithms.jl)) will provide significant performance improvements on larger graphs.
