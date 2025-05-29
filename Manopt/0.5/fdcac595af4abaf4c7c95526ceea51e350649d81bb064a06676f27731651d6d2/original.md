```
MeshAdaptiveDirectSearchState <: AbstractManoptSolverState
```

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `mesh_size`: the current (internal) mesh size
  * `scale_mesh`: the current scaling of the internal mesh size, yields the actual mesh size used
  * `max_stepsize`: an upper bound for the longest step taken in looking for a candidate in either poll or search
  * `poll_size`
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `poll::`[`AbstractMeshPollFunction`]: a poll step (functor) to perform
  * `search::`[`AbstractMeshSearchFunction`}(@ref) a search step (functor) to perform
