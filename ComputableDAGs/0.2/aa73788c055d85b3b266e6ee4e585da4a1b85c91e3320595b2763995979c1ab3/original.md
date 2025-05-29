```
NodeReduction <: Operation
```

The NodeReduction operation. Represents the reduction of two or more nodes with one another. Only one of the input nodes is kept, while all others are deleted and their parents are accumulated in the kept node's parents instead.

After the node reduction is applied, the graph has `length(nr.input) - 1` fewer nodes.

# Requirements for successful application

A vector of nodes can be reduced if:

  * All nodes are in the graph.
  * All nodes have the same task type.
  * All nodes have the same set of children.

[`is_valid_node_reduction_input`](@ref) can be used to `@assert` these requirements.

See also: [`can_reduce`](@ref)
