```
NeuralCDDE(model, tspan, hist, lags, alg = nothing, args...;
    sensealg = TrackerAdjoint(), kwargs...)
```

Constructs a neural delay differential equation (neural DDE) with constant delays.

Arguments:

  * `model`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the derivative function. Should take an input of size `[x; x(t - lag_1); ...; x(t - lag_n)]` and produce and output shaped like `x`.
  * `tspan`: The timespan to be solved on.
  * `hist`: Defines the history function `h(u, p, t)` for values before the start of the integration. Note that `u` is supposed to be used to return a value that matches the size of `u`.
  * `lags`: Defines the lagged values that should be utilized in the neural network.
  * `alg`: The algorithm used to solve the ODE. Defaults to `nothing`, i.e. the default algorithm from DifferentialEquations.jl.
  * `sensealg`: The choice of differentiation algorithm used in the backpropogation. Defaults to using reverse-mode automatic differentiation via Tracker.jl
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.
