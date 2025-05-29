```
identify_edges(hyper::HyperGraphProjection, node_vectors::Vector{Vector{OptiNode}})
```

Identify induced edges and edge separators from a vector of optinode partitions.

# Arguments

  * `hyper::HyperGraphProjection`: A `HyperGraphProjection` obtained from `hyper_projection`.
  * `node_vectors::Vector{Vector{OptiNode}}`: A vector of vectors that contain `OptiNode`s.

# Returns

  * partition_optiedges::Vector{Vector{OptiEdge}}: The `OptiEdge` vectors for each partition.
  * cross_optiedges::Vector{OptiEdge}: A vector of optiedges that cross partitions.
