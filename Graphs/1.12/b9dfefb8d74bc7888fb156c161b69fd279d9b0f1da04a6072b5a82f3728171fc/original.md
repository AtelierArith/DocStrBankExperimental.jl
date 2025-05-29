```
gdistances(g, source; sort_alg=QuickSort)
```

Return a vector filled with the geodesic distances of vertices in  `g` from `source`. If `source` is a collection of vertices each element should be unique. For vertices in disconnected components the default distance is `typemax(T)`.

An optional sorting algorithm may be specified (see Performance section).

### Performance

`gdistances` uses `QuickSort` internally for its default sorting algorithm, since it performs the best of the algorithms built into Julia Base. However, passing a `RadixSort` (available via [SortingAlgorithms.jl](https://github.com/JuliaCollections/SortingAlgorithms.jl)) will provide significant performance improvements on larger graphs.
