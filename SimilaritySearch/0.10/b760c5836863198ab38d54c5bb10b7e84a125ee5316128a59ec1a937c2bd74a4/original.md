```
searchbatch(index, Q, KNN::AbstractVector{KnnResult}; minbatch=0, pools=getpools(index)) -> indices, distances
```

Searches a batch of queries in the given index using an array of KnnResult's; each KnnResult object can specify different `k` values.

# Arguments

  * `minbatch`: Minimum number of queries solved per each thread, see [`getminbatch`](@ref)
  * `pools`: relevant for special databases or distance functions.    In most case uses the default is enought, but different pools should be used when indexes use other indexes internally to solve queries.   It should be an array of `Threads.nthreads()` preallocated `KnnResult` objects used to reduce memory allocations.
