```
PBVISolver <: Solver
```

Options dictionary for Point-Based Value Iteration for POMDPs.

# Fields

  * `max_iterations::Int64` the maximal number of iterations the solver runs. Default: 10
  * `ϵ::Float64` the maximal gap between alpha vector improve steps. Default = 0.01
  * `verbose::Bool` switch for solver text output. Default: false
