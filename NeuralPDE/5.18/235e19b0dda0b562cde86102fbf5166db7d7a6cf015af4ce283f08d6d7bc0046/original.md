```
neural_adapter(loss, init_params, pde_system, strategy)
```

Trains a neural network using the results from one already obtained prediction.

## Positional Arguments

  * `loss`: the body of loss function,
  * `init_params`: the initial parameter of the neural network,
  * `pde_system`: PDEs are defined using the ModelingToolkit.jl,
  * `strategy`: determines which training strategy will be used.
