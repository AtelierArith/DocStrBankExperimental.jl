```
searchbatch(index, Q, k::Integer; minbatch=0, pools=GlobalKnnResult) -> indices, distances
```

Searches a batch of queries in the given index (searches for k neighbors).

# Arguments

  * `index`: The search structure
  * `Q`: The set of queries
  * `k`: The number of neighbors to retrieve

# Keyword arguments

  * `minbatch` specifies how many queries are solved per thread.

      * Integers $1 ≤ minbatch ≤ |Q|$ are valid values
      * Set `minbatch=0` to compute a default number based on the number of available cores.
      * Set `minbatch=-1` to avoid parallelism.
  * `pools` relevant for special databases or distance functions.    In most case uses the default is enought, but different pools should be used when indexes use other indexes internally to solve queries.   It should be an array of `Threads.nthreads()` preallocated `KnnResult` objects used to reduce memory allocations.

Note: The i-th column in indices and distances correspond to the i-th query in `Q` Note: The final indices at each column can be `0` if the search process was unable to retrieve `k` neighbors.
