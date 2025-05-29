```
GridAM(kwargs...)
```

Maximizes the acquisition function by checking a fine grid of points from the domain.

Extremely simple optimizer which can be used for simple problems or for debugging. Not suitable for problems with high dimensional domain.

Can be used with constraints on `x`.

# Keywords

  * `problem::BossProblem`: Provide your defined optimization problem.
  * `steps::Vector{Float64}`: Defines the size of the grid gaps in each `x` dimension.
  * `parallel::Bool`: If `parallel=true`, the optimization is parallelized. Defaults to `true`.
  * `shuffle::Bool`: If `shuffle=true`, the grid points are shuffled before each optimization. Defaults to `true`.
