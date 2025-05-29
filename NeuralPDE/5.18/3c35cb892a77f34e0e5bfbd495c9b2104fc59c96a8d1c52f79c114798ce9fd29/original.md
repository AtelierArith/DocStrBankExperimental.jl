```
PINOODE(chain,
    opt,
    bounds;
    init_params = nothing,
    strategy = nothing
    kwargs...)
```

Algorithm for solving paramentric ordinary differential equations using a physics-informed neural operator, which is used as a solver for a parametrized `ODEProblem`.

## Positional Arguments

  * `chain`: A neural network architecture, defined as a `AbstractLuxLayer` or `Flux.Chain`.                `Flux.Chain` will be converted to `Lux` using `adapt(FromFluxAdaptor(false, false), chain)`
  * `opt`: The optimizer to train the neural network.
  * `bounds`: A dictionary containing the bounds for the parameters of the parametric ODE.
  * `number_of_parameters`: The number of points of train set in parameters boundaries.

## Keyword Arguments

  * `init_params`: The initial parameters of the neural network. By default, this is `nothing`,                            which thus uses the random initialization provided by the neural network library.
  * `strategy`: The strategy for training the neural network.
  * `additional_loss`: additional loss function added to the default one. For example, add training on data.
  * `kwargs`: Extra keyword arguments are splatted to the Optimization.jl `solve` call.

## References

  * Sifan Wang "Learning the solution operator of parametric partial differential equations with physics-informed DeepOnets"
  * Zongyi Li "Physics-Informed Neural Operator for Learning Partial Differential Equations"
