```
randomwalk!(agent, model::ABM{<:AbstractGridSpace}, r::Real = 1; kwargs...)
```

Move `agent` for a distance `r` in a random direction respecting boundary conditions and space metric. For Chebyshev and Manhattan metric, the step size `r` is rounded to  `floor(Int,r)`; for Euclidean metric in a GridSpace, random walks are ill defined  and hence not supported.

For example, for `Chebyshev` metric and `r=1`, this will move the agent with equal probability to any of the 8 surrounding cells. For Manhattan metric, it will move to any of the 4 surrounding cells.

## Keywords

  * `ifempty` will check that the target position is unoccupied and only move if that's true. So if `ifempty` is true, this can result in the agent not moving even if there are available  positions. By default this is true, set it to false if different agents can occupy the same  position. In a `GridSpaceSingle`, agents cannot overlap anyways and this keyword has no effect.
  * `force_motion` has an effect only if `ifempty` is true or the space is a `GridSpaceSingle`.  If set to true, the search for the random walk will be done only on the empty positions,  so in this case the agent will always move if there is at least one empty position to choose from.  By default this is false.
