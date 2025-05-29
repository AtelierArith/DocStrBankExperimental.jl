```
move_along_route!(agent, model::ABM{<:ContinuousSpace{D}}, pathfinder::AStar{D}, speed, dt = 1.0)
```

Move `agent` for one step along the route toward its target set by [`plan_route!`](@ref) at the given `speed` and timestep `dt`.

For pathfinding in models with [`ContinuousSpace`](@ref)

If the agent does not have a precalculated path or the path is empty, it remains stationary.
