```
Hyperparameters(; current_epoch::Int64 = 1, current_minibatch::Int64 = 1, loss_history::Vector{Float64} = Vector{Float64}(), optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule} = BFGS(initial_stepnorm=0.001), loss_epoch::Float64 = 0.0, epochs::Int64 = 50, batch_size::Int64 = 15)
```

Constructs a `Hyperparameters` object with the specified parameters.

# Arguments

  * `current_epoch::Int64`: The current epoch number. Defaults to 1.
  * `current_minibatch::Int64`: The current minibatch number. Defaults to 1.
  * `loss_history::Vector{Float64}`: A vector to store the history of loss values. Defaults to an empty vector.
  * `optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule}`: The optimizer to be used. Defaults to `BFGS(initial_stepnorm=0.001)`.
  * `loss_epoch::Float64`: The loss value for the current epoch. Defaults to 0.0.
  * `epochs::Int64`: The total number of epochs. Defaults to 50.
  * `batch_size::Int64`: The size of each minibatch. Defaults to 15.

# Returns

  * A `Hyperparameters` object initialized with the provided values.
