```
dbscan_label(tree::AbstractMatrix{<:Real}, radius::Real; min_neighbors::Int64 = 1, min_cluster_size::Int64 = 1)
```

Get predicted labels from density-based spatial clustering of applications with noise for a group of phylogenetic trees.

# Arguments

  * `tree`: a B * N tree Matrix (each column of tree Matrix is a B-dimensional tree in bipartiton format) and B < N.
  * `radius`: neighborhood radius; points within this distance are considered neighbors.
  * `min_neighbors`: minimal number of neighbors required to assign a point to a cluster.
  * `min_cluster_size`: minimal number of points in a cluster.

# Output

A `Vector` object with length of N containing predicted labels for each tree (the cluster it belongs to).      0 means the tree is noise.
