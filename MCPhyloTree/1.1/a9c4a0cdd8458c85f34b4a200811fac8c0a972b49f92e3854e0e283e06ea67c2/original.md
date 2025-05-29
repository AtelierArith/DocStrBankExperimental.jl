```
function create_tree_from_leaves(rng::Random.AbstractRNG, leaf_nodes::Vector{String}, rooted::Bool=false<:AbstractNode
```

Build a random tree from a list of leaf names. The tree is unrooted by default.

Returns the root node of the new tree.

  * `leaf_nodes` : A list of strings which are used as the names of the leaves.
  * `rooted` : Boolean indicating if the tree should be rooted
