```
NodeSplit <: Operation
```

The NodeSplit operation. Represents the split of its input node into one node for each of its parents. It is the reverse operation to the [`NodeReduction`](@ref).

# Requirements for successful application

A node can be split if:

  * It is in the graph.
  * It has at least 2 parents.

[`is_valid_node_split_input`](@ref) can be used to `@assert` these requirements.

See also: [`can_split`](@ref)
