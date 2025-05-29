```
BackwardPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(:backward),
    search_noise::Union{Nothing,Float64} = nothing,
    g_mult::Float32 = 1.0f0,
    h_mult::Float32 = 1.0f0,
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    fail_fast::Bool = false,
    save_search::Bool = false,
    save_search_order::Bool = save_search,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

Heuristic-guided backward (i.e. regression) search planner. Instead of searching forwards, searches backwards from the goal, which is treated as a *set* of  states which satisfy the goal predicates (equivalently, a *partial* state,  because only some predicates and fluents may be specified). Each expanded node also corresponds to a partial state. [1]

As with [`ForwardPlanner`](@ref), each node $n$ is expanded in order of increasing priority $f(n)$, defined as:

$$
f(n) = g_\text{mult} \cdot g(n) + h_\text{mult} \cdot h(n)
$$

However $g(n)$ is instead defined as the path cost from the goal to the current node $n$, and $h(n)$ is a heuristic estimate of the distance from the initial state. As such, only certain heuristics, such as [`GoalCountHeuristic`](@ref) and  [`HSPRHeuristic`](@ref) can be used with backward search.

Returns a [`PathSearchSolution`](@ref) or [`NullSolution`](@ref), similar to [`ForwardPlanner`](@ref).

This planner does not currently support domains with non-Boolean fluents or  problems involving constraint specifications.

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).

# Arguments

  * `heuristic`: Search heuristic that estimates cost of a state to the goal.
  * `search_noise`: Amount of Boltzmann search noise (`nothing` for deterministic search).
  * `g_mult`: Path cost multiplier when computing the $f$ value of a search node.
  * `h_mult`: Heuristic multiplier when computing the $f$ value of a search node.
  * `max_nodes`: Maximum number of search nodes before termination.
  * `max_time`: Maximum time in seconds before planner times out.
  * `fail_fast`: Flag to terminate search if the heuristic estimates an infinite cost.
  * `save_search`: Flag to save the search tree and frontier in the returned solution.
  * `save_search_order`: Flag to save the node expansion order in the returned solution.
  * `verbose`: Flag to print debug information during search.
  * `callback`: Callback function for logging, etc.
