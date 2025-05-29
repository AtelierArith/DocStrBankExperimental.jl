```
searchbatch(index, Q, I::AbstractMatrix{Int32}, D::AbstractMatrix{Float32}; minbatch=0, pools=getpools(index)) -> indices, distances
```

Searches a batch of queries in the given index and `I` and `D` as output (searches for `k=size(I, 1)`)

# Arguments

  * `index`: The search structure
  * `Q`: The set of queries
  * `k`: The number of neighbors to retrieve

# Keyword arguments

  * `minbatch`: Minimum number of queries solved per each thread, see [`getminbatch`](@ref)
  * `pools`: relevant for special databases or distance functions.    In most case uses the default is enought, but different pools should be used when indexes use other indexes internally to solve queries.   It should be an array of `Threads.nthreads()` preallocated `KnnResult` objects used to reduce memory allocations.
