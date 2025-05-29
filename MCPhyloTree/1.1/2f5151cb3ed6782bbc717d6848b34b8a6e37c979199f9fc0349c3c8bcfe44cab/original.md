```
prune_tree!(root::T, node_names::Vector{T})::Nothing where T<:AbstractNode
```

In-place version of prune_tree.

  * `root` : root node of tree to prune.
  * `node_names`: vector of Node objects to be removed from tree.
