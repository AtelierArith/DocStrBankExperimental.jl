```
allknn(g::AbstractSearchIndex, context, k::Integer; minbatch=0, pools=getpools(g)) -> knns, dists
allknn(g, context, knns, dists; minbatch=0, pools=getpools(g)) -> knns, dists
```

Computes all the k nearest neighbors (all vs all) using the index `g`. It removes self references.

# Parameters:

  * `g`: the index
  * `context`: the index's context (caches, hyperparameters, logger, etc)
  * Query specification and result:

      * `k`: the number of neighbors to retrieve
      * `knns`: an uninitialized integer matrix of (k, n) size for storing the `k` nearest neighbors of the `n` elements
      * `dists`: an uninitialized floating point matrix of (k, n) size for storing the `k` nearest distances of the `n` elements
  * `context`: caches, hyperparameters and meta specifications, e.g., see [`SearchGraphContext`](@ref)

# Returns:

  * `knns` a (k, n) matrix of identifiers; the i-th column corresponds to the i-th object in the dataset.   Zeros can happen to the end of each column meaning that the retrieval was less than the desired `k`
  * `dists` a (k, n) matrix of distances; the i-th column corresponds to the i-th object in the dataset.   Zero values in `knns` should be ignored in `dists`

# Note:

This function was introduced in `v0.8` series, and removes self references automatically. In `v0.9` the self reference is kept since removing from the algorithm introduces a considerable overhead.    
