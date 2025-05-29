```
execute!(
    sim::Simulation,
    solver;
    kwargs...
)
```

Solves the time-domain dynamic simulation model.

# Arguments

  * `sim::Simulation` : Initialized simulation object
  * `solver` : Solver used for numerical integration. Must be passed correctly depending on the Type of Simulation Model
  * `enable_progress_bar::Bool` : Default: `true`. Enables progress bar for the integration routine.
  * Additional solver keyword arguments can be included. See [Common Solver Options](https://diffeq.sciml.ai/stable/basics/common_solver_opts/) in the `DifferentialEquations.jl` documentation for more details.
