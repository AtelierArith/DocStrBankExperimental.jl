```
mutable struct Hyperparameters{F <: AbstractFloat, I <: Int} <: AbstractParameters
```

A mutable struct that holds hyperparameters for training a machine learning model.

# Keyword arguments

  * `current_epoch::I`: The current epoch number.
  * `current_minibatch::I`: The current minibatch number.
  * `loss_history::Vector{F}`: A vector storing the history of loss values.
  * `optimizer::Union{Optim.FirstOrderOptimizer, Flux.Optimise.AbstractOptimiser, Optimisers.AbstractRule}`: The optimizer used for training.
  * `loss_epoch::F`: The loss value for the current epoch.
  * `epochs::I`: The total number of epochs for training.
  * `batch_size::I`: The size of each minibatch.
