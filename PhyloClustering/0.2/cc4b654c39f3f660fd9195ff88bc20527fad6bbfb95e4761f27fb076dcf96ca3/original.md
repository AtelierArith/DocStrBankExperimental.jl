```
kmeans_label(tree::AbstractMatrix{<:Real}, n::Int64; init::String="k-means++", rng::AbstractRNG=Random.GLOBAL_RNG)
```

Get predicted labels from Yinyang K-means clustering for a group of phylogenetic trees.

# Arguments

  * `tree`: a B * N tree Matrix (each column of tree Matrix is a B-dimensional tree in bipartiton format).
  * `n`: the number of clusters.
  * `init`(defaults to `k-means++`): is one of the algorithms used for initialization.  Alternatively, one can use `rand` to choose random points for init.
  * `rng`: RNG object.

# Output

A `Vector` object with length of N containing predicted labels for each tree (the cluster it belongs to).
