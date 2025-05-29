```
ForwardPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(),
    search_noise::Union{Nothing,Float64} = nothing,
    g_mult::Float32 = 1.0f0,
    h_mult::Float32 = 1.0f0,
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    fail_fast::Bool = false,
    refine_method::Symbol = :continue,
    reset_node_count::Bool = true,
    save_search::Bool = true,
    save_search_order::Bool = true,
    save_parents::Bool = false,
    save_children::Bool = false,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

Forward best-first search planner, which encompasses uniform-cost search, greedy search, and A* search. Each node $n$ is expanded in order of increasing priority $f(n)$, defined as:

$$
f(n) = g_\text{mult} \cdot g(n) + h_\text{mult} \cdot h(n)
$$

where $g(n)$ is the path cost from the initial state to $n$, and $h(n)$ is the heuristic's goal distance estimate.

Returns a [`PathSearchSolution`](@ref) if the goal is achieved, containing a plan that reaches the goal node, and `status` set to `:success`. If the node or time budget runs out, the solution will instead contain a partial plan to the last node selected for expansion, with `status` set to `:max_nodes` or `:max_time` accordingly.

If `save_search` is true, the returned solution will contain the search tree and frontier so far. If `save_search` is true and the search space is exhausted return a `NullSolution` with `status` set to `:failure`.

# Arguments

  * `heuristic`: Search heuristic that estimates cost of a state to the goal.
  * `search_noise`: Amount of Boltzmann search noise (`nothing` for deterministic search).
  * `g_mult`: Path cost multiplier when computing the $f$ value of a search node.
  * `h_mult`: Heuristic multiplier when computing the $f$ value of a search node.
  * `max_nodes`: Maximum number of search nodes before termination.
  * `max_time`: Maximum time in seconds before planner times out.
  * `fail_fast`: Flag to terminate search if the heuristic estimates an infinite cost.
  * `refine_method`: Solution refinement method (one of `:continue`, `:reroot`, `:restart`)
  * `reset_node_count`: Whether to reset the expanded node count before solution refinement.
  * `save_search`: Flag to save the search tree and frontier (needed for refinement).
  * `save_search_order`: Flag to save the node expansion order in the solution.
  * `save_parents`: Flag to save all parent pointers in search tree (needed for rerooting).
  * `save_children`: Flag to save all children pointers in search tree (needed for rerooting).
  * `verbose`: Flag to print debug information during search.
  * `callback`: Callback function for logging, etc.

# Refinement Methods

Setting the `refine_method` keyword argument controls the behavior of [`refine!`](@ref) when called on a [`PathSearchSolution`](@ref):

  * `:continue` (default): Continues the search by expanding the search tree rooted at the original starting state. `save_search` will default to `true` if this method is used.
  * `:reroot`: Reroots the search tree at the newly-provided starting state, then continues the search, as in Fringe-Retrieving A* [1]. `save_search`, `save_parents`, and `save_children` will default to `true` if this method is used.
  * `:restart`: Restarts the search from the new starting state, throwing away the  previous search tree and frontier. This is the only valid refinement method when `save_search` is `false`.

[1] X. Sun, W. Yeoh, and S. Koenig, “Generalized Fringe-Retrieving A*: Faster moving target search on state lattices,” AAMAS (2010), pp. 1081-1088. [https://dl.acm.org/doi/abs/10.5555/1838206.1838352](https://dl.acm.org/doi/abs/10.5555/1838206.1838352)
