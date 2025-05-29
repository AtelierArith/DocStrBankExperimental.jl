```
is_valid(graph::DAG, node::ComputeTaskNode)
```

Verify that the given compute node is valid in the graph. Call with `@assert` or `@test` when testing or debugging.

This also calls [`is_valid_node(graph::DAG, node::Node)`](@ref).
