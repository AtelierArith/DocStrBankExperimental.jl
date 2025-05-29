```
move_along_route!(agent, model::ABM{<:GridSpace{D}}, pathfinder::AStar{D})
```

Move `agent` for one step along the route toward its target set by [`plan_route!`](@ref)

For pathfinding in models with [`GridSpace`](@ref).

If the agent does not have a precalculated path or the path is empty, it remains stationary.
