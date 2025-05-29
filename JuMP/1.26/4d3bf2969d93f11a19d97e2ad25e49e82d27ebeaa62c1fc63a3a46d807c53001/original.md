```
 print_bridge_graph([io::IO,] model::GenericModel)
```

Print the hyper-graph containing all variable, constraint, and objective types that could be obtained by bridging the variables, constraints, and objectives that are present in the model.

!!! warning
    This function is intended for advanced users. If you want to see only the bridges that are currently used, use [`print_active_bridges`](@ref) instead.


## Explanation of output

Each node in the hyper-graph corresponds to a variable, constraint, or objective type.

  * Variable nodes are indicated by `[ ]`
  * Constraint nodes are indicated by `( )`
  * Objective nodes are indicated by `| |`

The number inside each pair of brackets is an index of the node in the hyper-graph.

Note that this hyper-graph is the full list of possible transformations. When the bridged model is created, we select the shortest hyper-path(s) from this graph, so many nodes may be un-used.

For more information, see Legat, B., Dowson, O., Garcia, J., and Lubin, M. (2020).  "MathOptInterface: a data structure for mathematical optimization problems." URL: [https://arxiv.org/abs/2002.03447](https://arxiv.org/abs/2002.03447)
