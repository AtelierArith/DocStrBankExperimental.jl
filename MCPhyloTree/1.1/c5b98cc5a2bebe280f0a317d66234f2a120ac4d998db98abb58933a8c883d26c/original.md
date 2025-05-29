```
upgma(dm::Array{Float64,2}, Array{String,1})
```

This function returns a phylogenetic tree by using UPGMA based on a given distance matrix and an array of leaf names.

Returns a node of the resulting tree, from which it can be traversed.

  * `dm` : Matrix from which to create the tree.
  * `leaf_names` : array of strings containing names of leaf nodes.
