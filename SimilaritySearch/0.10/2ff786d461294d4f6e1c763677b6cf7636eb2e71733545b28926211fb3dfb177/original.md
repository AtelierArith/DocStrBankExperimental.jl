```
allknn(g::AbstractSearchIndex, k::Integer; minbatch=0, pools=getpools(g)) -> knns, dists
allknn(g, knns, dists; minbatch=0, pools=getpools(g)) -> knns, dists
```

Computes all the k nearest neighbors (all vs all) using the index `g`. It removes self references.

# Parameters:

  * `g`: the index
  * Query specification and result:

      * `k`: the number of neighbors to retrieve
      * `knns`: an uninitialized integer matrix of (k, n) size for storing the `k` nearest neighbors of the `n` elements
      * `dists`: an uninitialized floating point matrix of (k, n) size for storing the `k` nearest distances of the `n` elements
  * `minbatch`: controls how multithreading is used for evaluating configurations, see [`getminbatch`](@ref)
  * `pools`: A pools object, dependent of `g`

# Returns:

  * `knns` a (k, n) matrix of identifiers; the i-th column corresponds to the i-th object in the dataset.   Zeros can happen to the end of each column meaning that the retrieval was less than the desired `k`
  * `dists` a (k, n) matrix of distances; the i-th column corresponds to the i-th object in the dataset.   Zero values in `knns` should be ignored in `dists`

# Keyword arguments

  * `minbatch`: controls how multithreading is used for evaluating configurations, see [`getminbatch`](@ref)
  * `pools`: `pools`: A pools object, dependent of `g`

# Note:

This function was introduced in `v0.8` series, and removes self references automatically. In `v0.9` the self reference is kept since removing from the algorithm introduces a considerable overhead.    
