```
Hclust{T<:Real}
```

The output of [`hclust`](@ref), hierarchical clustering of data points.

Provides the bottom-up definition of the dendrogram as the sequence of merges of the two lower subtrees into a higher level subtree.

This type mostly follows R's `hclust` class.

# Fields

  * `merges::Matrix{Int}`: $N×2$ matrix encoding subtree merges:

      * each row specifies the left and right subtrees (referenced by their $id$s) that are merged
      * negative subtree $id$ denotes the leaf node and corresponds to the data point at position $-id$
      * positive $id$ denotes nontrivial subtree (the row `merges[id, :]` specifies its left and right subtrees)
  * `linkage::Symbol`: the name of *cluster linkage* function used to construct the hierarchy (see [`hclust`](@ref))
  * `heights::Vector{T}`: subtree heights, i.e. the distances between the left  and right branches of each subtree calculated using the specified `linkage`
  * `order::Vector{Int}`: the data point indices ordered so that there are no  intersecting branches on the *dendrogram* plot. This ordering also puts  the points of the same cluster close together.

See also: [`hclust`](@ref).
