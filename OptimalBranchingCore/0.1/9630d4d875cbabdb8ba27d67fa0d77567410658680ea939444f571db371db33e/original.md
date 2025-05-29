```
LPSolver <: AbstractSetCoverSolver
LPSolver(; optimizer = HiGHS.Optimizer, max_itr::Int = 20, γ0::Float64 = 2.0, verbose::Bool = false)
```

A linear programming solver for set covering problems.

### Fields

  * `optimizer`: The optimizer to be used.
  * `max_itr::Int`: The maximum number of iterations to be performed.
  * `γ0::Float64`: The initial γ value.
  * `verbose::Bool`: Whether to print the solver's output.
