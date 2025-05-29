```
plan_best_route!(agent, dests, pathfinder::AStar{D}; kwargs...)
```

Calculate, store, and return the best path to move the agent from its current position to a chosen destination taken from `dests` using `pathfinder`.

The `condition = :shortest` keyword returns the shortest path which is shortest out of the possible destinations. Alternatively, the `:longest` path may also be requested.

Return the position of the chosen destination. Return `nothing` if none of the supplied destinations are reachable.
