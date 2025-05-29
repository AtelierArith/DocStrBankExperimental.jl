```
dists, inds = sparse_distmat(y::Vector{<:AbstractVector{T}}, k, dist, radius; kwargs...) where T
```

Compute the `k` nearest neighbors between signals in `y`, corresponding to the `k` smallest entries in each row of the pairwise distance matrix. The return values are vectors of length-k vectors with the calculated distances and neighbor indices.

#Arguments:

  * `y`: Vector of vectors containing the signals
  * `k`: number of neighbors
  * `dist`: the inner metric, e.g., `SqEuclidean()`
  * `kwargs`: these are sent to `dtw_cost`.
  * `showprogress = true`
