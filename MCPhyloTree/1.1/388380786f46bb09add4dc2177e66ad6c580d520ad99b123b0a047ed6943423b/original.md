```
prune_tree!(root::T, node_names::Vector{String})::Nothing where T<:AbstractNode
```

In-place version of prune_tree.

  * `root` : root Node of tree to prune.
  * `node_names` : vector of strings, used to specify nodes to remove.
