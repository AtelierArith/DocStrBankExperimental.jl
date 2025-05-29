```
NeuralODE(model, tspan, alg = nothing, args...; kwargs...)
```

Constructs a continuous-time recurrant neural network, also known as a neural ordinary differential equation (neural ODE), with a fast gradient calculation via adjoints [1]. At a high level this corresponds to solving the forward differential equation, using a second differential equation that propagates the derivatives of the loss backwards in time.

Arguments:

  * `model`: A `Flux.Chain` or `Lux.AbstractLuxLayer` neural network that defines the ̇x.
  * `tspan`: The timespan to be solved on.
  * `alg`: The algorithm used to solve the ODE. Defaults to `nothing`, i.e. the default algorithm from DifferentialEquations.jl.
  * `sensealg`: The choice of differentiation algorithm used in the backpropogation. Defaults to an adjoint method. See the [Local Sensitivity Analysis](https://docs.sciml.ai/SciMLSensitivity/stable/) documentation for more details.
  * `kwargs`: Additional arguments splatted to the ODE solver. See the [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) documentation for more details.

References:

[1] Pontryagin, Lev Semenovich. Mathematical theory of optimal processes. CRC press, 1987.
