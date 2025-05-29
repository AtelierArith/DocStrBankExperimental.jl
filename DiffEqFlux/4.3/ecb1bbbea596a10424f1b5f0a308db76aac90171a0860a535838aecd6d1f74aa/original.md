```
NeuralSDE(drift, diffusion, tspan, nbrown, alg = nothing, args...;
    sensealg=TrackerAdjoint(), kwargs...)
```

Constructs a neural stochastic differential equation (neural SDE).

Arguments:

  * `drift`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the drift function.
  * `diffusion`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the diffusion function. Should output a matrix that is `nbrown x size(x, 1)`.
  * `tspan`: The timespan to be solved on.
  * `nbrown`: The number of Brownian processes.
  * `alg`: The algorithm used to solve the ODE. Defaults to `nothing`, i.e. the default algorithm from DifferentialEquations.jl.
  * `sensealg`: The choice of differentiation algorithm used in the backpropogation.
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.
