```
neighbor_joining(dm::Array{Float64,2}, Array{String,1})
```

This function returns a phylogenetic tree by using neighbor-joining based on a given distance matrix and an array of leaf names.

Returns a node of the resulting tree, from which it can be traversed.

  * `dm` : Matrix used to create Tree.
  * `leaf_names` : Array containing names of leaf nodes.
