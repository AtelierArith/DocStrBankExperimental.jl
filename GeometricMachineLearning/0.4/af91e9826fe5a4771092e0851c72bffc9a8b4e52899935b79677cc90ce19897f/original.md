```
Optimizer(method, cache, step, retraction)
```

Store the `method` (e.g. [`AdamOptimizer`](@ref) with corresponding hyperparameters), the `cache` (e.g. [`AdamCache`](@ref)), the optimization step and the retraction.

It takes as input an optimization method and the parameters of a network. 

Before one can call `Optimizer` a [`OptimizerMethod`](@ref) that stores all the hyperparameters of the optimizer needs to be specified. 

# Functor

For an instance `o` of `Optimizer`, we can call the corresponding functor as:

```julia
o(nn, dl, batch, n_epochs, loss)
```

The arguments are:

1. `nn::NeuralNetwork`
2. `dl::`[`DataLoader`](@ref)
3. `batch::`[`Batch`](@ref)
4. `n_epochs::Integer`
5. `loss::NetworkLoss`

The last argument is optional for many neural network architectures. We have the following defaults:

  * A [`TransformerIntegrator`](@ref) uses [`TransformerLoss`](@ref).
  * A [`NeuralNetworkIntegrator`](@ref) uses [`FeedForwardLoss`](@ref).
  * An [`AutoEncoder`](@ref) uses [`AutoEncoderLoss`](@ref).

In addition there is an optional keyword argument that can be supplied to the functor:

  * `show_progress=true`: This specifies whether a progress bar should be shown during training.

# Implementation

Internally the functor for `Optimizer` calls [`GlobalSection`](@ref) once at the start and then [`optimize_for_one_epoch!`](@ref) for each epoch.
