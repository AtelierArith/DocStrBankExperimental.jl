```
AlternatingRealTimeHeuristicSearch(
    planners::RealTimeHeuristicSearch...;
    share_values::Bool = true,
    share_search::Bool = false,
    share_paths::Bool = true,
)
```

A variant of [`RealTimeHeuristicSearch`](@ref) (`AlternatingRTHS` or `ARTHS` for short) that alternates between different search strategies, corresponding to one or more `planners`. For example, `ARTHS` can alternate between a  `RTHS` planner that uses A* search (`h_mult = 1.0`) and an `RTHS` planner that  uses breadth-first search (`h_mult = 0.0`), ensuring that the updated region  of the state space is both deep and broad.

Returns a [`MultiSolution`](@ref) composed of [`ReusableTreePolicy`](@ref) sub-solutions. By default, these sub-solutions share and update the same value estimates (`share_values = true`) and the same reusable tree of optimal paths to the goal (`share_paths = true`), but do not share the same reusable forward search tree (`share_search = false`).
