A mutable struct that holds parameters for the solver.

```
SolverParameters{F <: AbstractFloat, I <: Integer}
```

# Fields

  * `solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm`: The algorithm used for solving differential equations.
  * `reltol::F`: The relative tolerance for the solver.
  * `step::F`: The step size for the solver.
  * `tstops::Union{Nothing, Vector{F}}`: Optional vector of time points where the solver should stop for the callbacks.
  * `save_everystep::Bool`: Flag indicating whether to save the solution at every step.
  * `progress::Bool`: Flag indicating whether to show progress during the solving process.
  * `progress_steps::I`: The number of steps between progress updates.
