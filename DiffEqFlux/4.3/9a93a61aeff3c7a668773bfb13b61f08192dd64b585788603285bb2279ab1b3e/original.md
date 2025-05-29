```
NeuralDAE(model, constraints_model, tspan, args...; differential_vars = nothing,
    sensealg = TrackerAdjoint(), kwargs...)
```

Constructs a neural differential-algebraic equation (neural DAE).

Arguments:

  * `model`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the derivative function. Should take an input of size `x` and produce the residual of `f(dx,x,t)` for only the differential variables.
  * `constraints_model`: A function `constraints_model(u,p,t)` for the fixed constraints to impose on the algebraic equations.
  * `tspan`: The timespan to be solved on.
  * `alg`: The algorithm used to solve the ODE. Defaults to `nothing`, i.e. the default algorithm from DifferentialEquations.jl.
  * `sensealg`: The choice of differentiation algorithm used in the backpropogation. Defaults to using reverse-mode automatic differentiation via Tracker.jl
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.
