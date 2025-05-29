```
AbstractMeshPollFunction
```

An abstract type for common “poll” strategies in the [`mesh_adaptive_direct_search`](@ref) solver. A subtype of this The functor has to fulfil

  * be callable as `poll!(problem, mesh_size; kwargs...)` and modify the state

as well as to provide functions

  * `is_successful(poll!)` that indicates whether the last poll was successful in finding a new candidate
  * `get_basepoint(poll!)` that returns the base point at which the mesh is build
  * `get_candidate(poll!)` that returns the last found candidate if the poll was successful. Otherwise the base point is returned
  * `get_descent_direction(poll!)` the the vector that points from the base point to the candidate. If the last poll was not successful, the zero vector is returned
  * `update_basepoint!(M, poll!, p)` that updates the base point to `p` and all necessary internal data to a new point to build a mesh at

The `kwargs...` could include

  * `scale_mesh=1.0`: to rescale the mesh globally
  * `max_stepsize=Inf`: avoid exceeding a step size beyond this value, e.g. injectivity radius. any vector longer than this should be shortened to the provided maximum step size.
