```
ReusableTreePolicy(
    value_policy::PolicySolution,
    search_sol::PathSearchSolution,
    [goal_tree::Dict{UInt, PathNode}]
)
```

The policy returned by [`RealTimeHeuristicSearch`](@ref), which stores a value table in the nested `value_policy`, a forward search tree in `search_sol`, and (when `reuse_paths` is `true`) a reusable `goal_tree` of cost-optimal paths to the goal.

When taking actions at states along some stored cost-optimal path, actions along that path are followed, as in Tree-Adaptive A* [1]. Otherwise, the highest value action according to `value_policy` is returned, with ties broken by  the (possibly incomplete) plan in `search_sol`.

[1] C. Hernández, X. Sun, S. Koenig, and P. Meseguer, "Tree Adaptive A*,"  AAMAS (2011), pp. 123–130. [https://dl.acm.org/doi/abs/10.5555/2030470.2030488](https://dl.acm.org/doi/abs/10.5555/2030470.2030488).
