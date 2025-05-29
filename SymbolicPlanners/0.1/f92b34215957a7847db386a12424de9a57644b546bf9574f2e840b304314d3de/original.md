```
RealTimeHeuristicSearch(;
    heuristic::Heuristic = GoalCountHeuristic(),
    n_iters::Int = 1,
    max_nodes::Int = 50,
    update_method::Symbol = :dijkstra,
    search_neighbors::Symbol = :unexpanded,
    save_search::Bool = true,
    reuse_search::Bool = false,
    reuse_paths::Bool = true,
    kwargs...
)

RealTimeHeuristicSearch(
    planner::ForwardPlanner,
    n_iters::Int = 1,
    update_method::Symbol = :dijkstra,
    search_neighbors::Symbol = :unexpanded,
    reuse_search::Bool = true,
    reuse_paths::Bool = true,
)
```

A real time heuristic search (`RTHS`) algorithm [1] similar to `RTDP`. Instead of greedy rollouts, forward heuristic search is performed from the current state (up to `max_nodes`), and value estimates are updated for all states in the interior of the search tree. Search may also be performed from neighboring states by configuring `search_neighbors`. A simulated action is then taken to the best neighboring state. This process repeats for `n_iters`, with future searches using the updated value function as a more informed heuristic.

Returns a [`ReusableTreePolicy`](@ref), containing a [`TabularVPolicy`](@ref) of state value estimates, the most recent [`PathSearchSolution`](@ref) produced by forward search (including a search tree if `save_search` is `true`), and a  reusable tree of goal paths if `reuse_paths` is `true`.

# Arguments

  * `planner`: The [`ForwardPlanner`](@ref) used for lookahead heuristic search. Any keyword arguments accepted by [`ForwardPlanner`](@ref) are also keyword arguments for `RTHS` (e.g. `heuristic`, `max_nodes`, `save_search`, etc.).
  * `n_iters`: Number of iterations to perform. In each iteration,  search is followed by a simulated action to the best neighboring state. If a goal or dead end is reached, we restart from the initial state.
  * `update_method`: Method used to update value estimates, either via  cost differencing from the terminal node (`:costdiff`), or via Dijkstra's algorithm (`:dijkstra`).
  * `search_neighbors`: Controls whether search is additionally performed from all neighbors of the current state (`:all`), from neighbors unexpanded by the initial search (`:unexpanded`), or none of them (`:none`).
  * `reuse_search`: If `true`, then previous search solutions are reused by subsequent searches in future iterations or calls to [`refine!`](@ref). The latter requires `save_search` to be `true`. Search solutions are reused via the `:reroot` refinement method for [`ForwardPlanner`](@ref).
  * `reuse_paths`: If `true`, then every time a path to the goal is found, it is stored in a reusable tree of goal paths, as in Tree Adaptive A* [2]. Future searches will terminate once a previous path is encountered, reducing the cost of search. A consistent `heuristic` is required to ensure path optimality.

# Update Methods

Setting the `update_method` keyword argument controls how value estimates $V(s)$ (or equivalently, cost-to-goal estimates $h(s) = -V(s)$) are updated:

  * `:costdiff`: Value estimates are updated by cost differencing from the terminal node $t$. For each node $s$ in the search tree's interior, we estimate the cost-to-goal $h(s)$ by adding a lower bound on the cost from $s$ to $t$ to the cost-to-goal of $t$:

    $$
    h(s) = h(t) + (c(r, t) - c(r, s))
    $$

    where $c(r, s)$ is the cost from the root node $r$ to $s$. This is the update used by Real-Time Adaptive A* [3]. Takes $O(N)$ time, where $N$ is the size of the tree's interior.
  * `:dijkstra` : Value estimates are backpropagated from the search frontier via Dijkstra's algorithm. For each node $s$ in tree's interior, we update the cost-to-goal $h(s)$ by minimizing over all paths to the frontier:

    $$
    h(s) = \min_{t \in F} h(t) + c(s, t)
    $$

    This is the update rule by LSS-LRTA* [4], which produces more informed value estimates than `:costdiff`, but takes $O(NB \log NB)$ time. $N$ is the size of the tree's interior and $B$ is the maximal branching factor.  The `save_parents` keyword for [`ForwardPlanner`](@ref) defaults to `true` when this method is used.

Both of these update methods require a `heuristic` that is initially consistent for the updated value estimates to remain consistent.

[1] R. E. Korf, "Real-Time Heuristic Search," Artificial Intelligence, vol. 42, no. 2, pp. 189–211, Mar. 1990, [https://doi.org/10.1016/0004-3702(90)90054-4](https://doi.org/10.1016/0004-3702(90)90054-4).

[2] C. Hernández, X. Sun, S. Koenig, and P. Meseguer, "Tree Adaptive A*,"  AAMAS (2011), pp. 123–130. [https://dl.acm.org/doi/abs/10.5555/2030470.2030488](https://dl.acm.org/doi/abs/10.5555/2030470.2030488).

[3] S. Koenig and M. Likhachev, "Real-Time Adaptive A*," AAMAS (2006), pp. 281–288. [https://doi.org/10.1145/1160633.1160682](https://doi.org/10.1145/1160633.1160682).

[4] S. Koenig and X. Sun, "Comparing real-time and incremental heuristic search for real-time situated agents", AAMAS (2009), pp. 313–341. [https://dl.acm.org/doi/10.5555/1018410.1018838](https://dl.acm.org/doi/10.5555/1018410.1018838).
