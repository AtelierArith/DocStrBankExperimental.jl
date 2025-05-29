```
graph(problem_instance)
```

Generate the [`DAG`](@ref) for the given `problem_instance`. Every entry node (see [`get_entry_nodes`](@ref)) to the graph must have a name set. Implement [`input_expr`](@ref) to return a valid expression for each of those names.

For more details on the `problem_instance`, please refer to the documentation.
