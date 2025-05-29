```
fft(dist::SemiMetric, X::AbstractDatabase, k; verbose=true)
```

Selects `k` items far from each other based on Farthest First Traversal algorithm.

Returns a named tuple with the following fields:

  * `centers` contains the list of centers (indexes to $X$)
  * `nn` the id of the nearest center (in $X$ order, identifiers between 1 to `length(X))
  * `nndists` the distance from each object in the database to its nearest centers (in $X$ order)
  * `dmax` smallest distance among centers

Based on `enet.jl` from `KCenters.jl`
