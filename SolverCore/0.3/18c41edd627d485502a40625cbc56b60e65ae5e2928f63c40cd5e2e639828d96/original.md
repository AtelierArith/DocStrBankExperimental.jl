```
solve!(solver, model; kwargs...)
solve!(solver, model, stats; kwargs...)
```

Apply `solver` to `model`.

# Arguments

  * `solver::AbstractOptimizationSolver`: solver structure to hold all storage necessary for a solve
  * `model::AbstractNLPModel`: the model solved, see `NLPModels.jl`
  * `stats::GenericExecutionStats`: stats structure to hold solution information.

The first invocation allocates and returns a new `GenericExecutionStats`. The second one fills out a preallocated stats structure and allows for efficient re-solves.

The `kwargs` are passed to the solver.

# Return Value

  * `stats::GenericExecutionStats`: stats structure holding solution information.
