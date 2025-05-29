```
search(ss, query, t::SearchType [, skip]; kwargs... ) → idxs, ds
```

Perform a neighbor search in the search structure `ss` for the given `query` with search type `t` (see [`SearchType`](@ref)). Return the indices of the neighbors (in the original data) and the distances from the query. Available search types are:

  * [`NeighborNumber`](@ref)
  * [`WithinRange`](@ref)

Optional `skip` function takes as input the index of the found neighbor (in the original data) `skip(i)` and returns `true` if this neighbor should be skipped.

Package-specific keywords are possible.
