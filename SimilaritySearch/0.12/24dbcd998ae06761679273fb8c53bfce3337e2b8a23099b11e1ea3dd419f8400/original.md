```
searchbatch(index, ctx, Q, k::Integer) -> indices, distances
searchbatch(index, Q, k::Integer) -> indices, distances
```

Searches a batch of queries in the given index (searches for k neighbors).

# Arguments

  * `index`: The search structure
  * `Q`: The set of queries
  * `k`: The number of neighbors to retrieve
  * `context`: caches, hyperparameters, and meta data (defaults to `getcontext(index)`)

Note: The i-th column in indices and distances correspond to the i-th query in `Q` Note: The final indices at each column can be `0` if the search process was unable to retrieve `k` neighbors.
