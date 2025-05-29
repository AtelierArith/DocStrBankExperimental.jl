```
order_from_tree_decomposition(td::Dict{Symbol, Any}; root::Symbol=:b_1)
```

Return a vertex elimination order with the same treewidth as the given tree decompositon.

The algorithm used to construct the vertex elimination order is described by Shutski et al in the following paper https://doi.org/10.1103/PhysRevA.102.062614

# Keywords

  * `root::Symbol=:b_1`: The node of the tree to take as the root. Must be a symbol of the                      form `:b_n` where `n` is an integer between 1 and the number of bags                      in the tree decomposition.
