```
Workspace(problem::Problem; <keyword arguments>)
```

Create a workspace in which `problem` can be solved by calling [`step!`](@ref) or [`converge!`](@ref).

All optional arguments `arg` can also be set via `set_[arg]!(ws, ...)` after construction.

## Arguments

  * `eps = 1`. The Sinkhorn scaling parameter.
  * `rho = Inf`. The default value of the marginal penalty parameter `rho`.
  * `rhos`. Dictionary that maps nodes to `rho` values.
  * `weights`. Dictionary that maps edges to values that weight the cost.
  * `reach = Inf`. Reach parameter (radius of maximally allowed transport).
  * `logdomain = true`. Whether to work in the log or exp domain.
  * `stepmode = :stable`. Strategy that determines the order of potential updates. See the documentation of [`Workspace`](@ref) for details.
  * `atype = :array64`. Array type used in the backend.
