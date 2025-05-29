```
BreadthFirstPlanner(;
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    save_search::Bool = false,
    save_search_order::Bool = save_search,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

Breadth-first search planner. Nodes are expanded in order of increasing distance from the initial state (skipping previously visited nodes).

Returns a [`PathSearchSolution`](@ref) or [`NullSolution`](@ref), similar to [`ForwardPlanner`](@ref).

# Arguments

  * `max_nodes`: Maximum number of search nodes before termination.
  * `max_time`: Maximum time in seconds before planner times out.
  * `save_search`: Flag to save the search tree and frontier in the returned solution.
  * `save_search_order`: Flag to save the node expansion order in the returned solution.
  * `verbose`: Flag to print debug information during search.
  * `callback`: Callback function for logging, etc.
