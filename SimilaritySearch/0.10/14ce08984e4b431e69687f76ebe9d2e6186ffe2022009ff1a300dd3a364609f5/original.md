```
search(ex::ParallelExhaustiveSearch, q, res::KnnResult; minbatch=0, pools=nothing)
```

Solves the query evaluating all items in the given query.

# Arguments

  * `ex`: the search structure
  * `q`: the query to solve
  * `res`: the result set

# Keyword arguments

  * `minbatch`: Minimum number of queries solved per each thread, see [`getminbatch`](@ref)
  * `pools`: The set of caches (nothing for this index)
