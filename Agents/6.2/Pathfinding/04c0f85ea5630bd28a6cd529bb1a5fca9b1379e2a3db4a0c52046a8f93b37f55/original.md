```
plan_route!(agent, dest, pathfinder::AStar{D})
```

Calculate and store the shortest path to move the agent from its current position to `dest` (a position e.g. `(1, 5)` or `(1.3, 5.2)`) using the provided `pathfinder`.

Use this method in conjunction with [`move_along_route!`](@ref).
