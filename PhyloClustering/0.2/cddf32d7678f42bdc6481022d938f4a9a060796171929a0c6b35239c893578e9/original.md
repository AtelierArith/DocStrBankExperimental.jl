```
hc_label(matrix::AbstractMatrix{<:Real}, n::Int64; linkage::Symbol=:ward)
```

Get predicted labels from hierarchical clustering for a group of phylogenetic trees.

# Arguments

  * `matrix`: a N * N pairwise distance Matrix.
  * `n`: the number of clusters.
  * `linkage`(defaults to `:ward`): cluster linkage function to use. It affects what clusters are merged on each iteration:

      * `:single`: use the minimum distance between any of the cluster members
      * `:average`: use the mean distance between any of the cluster members
      * `:complete`: use the maximum distance between any of the members
      * `:ward`: the distance is the increase of the average squared distance of a point to its cluster centroid after merging the two clusters
      * `:ward_presquared`: same as `:ward`, but assumes that the distances in `d` are already squared.

# Output

A `Vector` object with length of N containing predicted labels for each tree (the cluster it belongs to). 
