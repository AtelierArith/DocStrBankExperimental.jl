```
neighbor_joining(dm::Array{Float64,2})
```

This function returns a phylogenetic tree by using neighbor-joining based on a given distance matrix. Creates an array of nodes to be used as leaves.

Returns a node of the resulting tree, from which it can be traversed.

  * `dm` : Matrix from which to create tree.
