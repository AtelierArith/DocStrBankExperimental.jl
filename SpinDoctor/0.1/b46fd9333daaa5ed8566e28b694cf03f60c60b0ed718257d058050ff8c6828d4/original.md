```
function solve(
    problem::BTPDE,
    gradient::ScalarGradient,
    odesolver::IntervalConstantSolver;
    callbacks = [],
)
```

Solve the Bloch-Torrey partial differential equation using P1 finite elements in space and a theta-rule in time. This time stepping scheme requires a degree of implicitness `θ` and a time step `Δt`:

  * `θ = 0.5`: Crank-Nicolson (second order)
  * `θ = 1.0`: Implicit Euler (first order)

The function only works for interval-wise constant `ScalarGradient`s, and errors otherwise.
