```
KMeansTreeNode{T} <: AbstractNode
```

Is the datatype of each node in the [K-Means Clustering Tree](@ref).

# Fields

  * `parent::Union{KMeansTreeNode{T},Nothing}`: is the superordinate cluster of   of the represented cluster
  * `children::Union{Vector{KMeansTreeNode{T}}, Nothing}`: all directly    subordinated clusters of the represented cluster
  * `level::Integer`: the level of the represented cluster
  * `center`: the center by which the cluster is defined
  * `radius`: the euclidian distance between the center and the farthest away   point
  * `data::T`: array containig the indices of the points in this cluster
