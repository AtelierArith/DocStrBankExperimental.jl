```
prune_tree(root::T, node_names::Vector{String})::T where T<:AbstractNode
```

This function removes specific nodes, including their descendants, from a tree.

  * `root` : root Node of tree to prune.
  * `node_names` : vector of strings, used to specify nodes to remove.
