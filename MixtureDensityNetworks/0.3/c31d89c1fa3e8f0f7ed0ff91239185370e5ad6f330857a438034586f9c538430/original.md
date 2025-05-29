```julia
fit!(
    m,
    X::Matrix{<:Real},
    Y::Matrix{<:Real};
    opt,
    batchsize,
    epochs,
    verbosity
) -> Tuple{Any, @NamedTuple{learning_curve::Vector{Float64}, best_epoch::Int64, best_loss::Float64}}

```

Fit the model to the data given by X and Y.

# Parameters

  * `m`: The model to be trained.
  * `X`: A dxn matrix where d is the number of input features and n is the number of samples.
  * `Y`: A dxn matrix where d is the dimension of the output and n is the number of samples.
  * `opt`: The optimization algorithm to use during training (default = Adam(1e-3)).
  * `batchsize`: The batch size for each iteration of gradient descent (default = 32).
  * `epochs`: The number of epochs to train for (default = 100).
  * `verbosity`: Whether to show a progress bar (default = 1) or not (0).
