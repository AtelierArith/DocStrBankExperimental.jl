```
PhysicsInformedNN(chain, strategy; init_params = nothing, phi = nothing,
                  param_estim = false, additional_loss = nothing,
                  adaptive_loss = nothing, logger = nothing, log_options = LogOptions(),
                  iteration = nothing, kwargs...)
```

A `discretize` algorithm for the ModelingToolkit PDESystem interface, which transforms a `PDESystem` into an `OptimizationProblem` using the Physics-Informed Neural Networks (PINN) methodology.

## Positional Arguments

  * `chain`: a vector of Lux/Flux chains with a d-dimensional input and a 1-dimensional output          corresponding to each of the dependent variables. Note that this specification          respects the order of the dependent variables as specified in the PDESystem.          Flux chains will be converted to Lux internally using          `adapt(FromFluxAdaptor(), chain)`.
  * `strategy`: determines which training strategy will be used. See the Training Strategy             documentation for more details.

## Keyword Arguments

  * `init_params`: the initial parameters of the neural networks. If `init_params` is not given, then the neural network default parameters are used. Note that for Lux, the default will convert to Float64.
  * `phi`: a trial solution, specified as `phi(x,p)` where `x` is the coordinates vector for the dependent variable and `p` are the weights of the phi function (generally the weights of the neural network defining `phi`). By default, this is generated from the `chain`. This should only be used to more directly impose functional information in the training problem, for example imposing the boundary condition by the test function formulation.
  * `adaptive_loss`: the choice for the adaptive loss function. See the [adaptive loss page](@ref adaptive_loss) for more details. Defaults to no adaptivity.
  * `additional_loss`: a function `additional_loss(phi, θ, p_)` where `phi` are the neural network trial solutions, `θ` are the weights of the neural network(s), and `p_` are the hyperparameters of the `OptimizationProblem`. If `param_estim = true`, then `θ` additionally contains the parameters of the differential equation appended to the end of the vector.
  * `param_estim`: whether the parameters of the differential equation should be included in the values sent to the `additional_loss` function. Defaults to `false`.
  * `logger`: ?? needs docs
  * `log_options`: ?? why is this separate from the logger?
  * `iteration`: used to control the iteration counter???
  * `kwargs`: Extra keyword arguments which are splatted to the `OptimizationProblem` on `solve`.
