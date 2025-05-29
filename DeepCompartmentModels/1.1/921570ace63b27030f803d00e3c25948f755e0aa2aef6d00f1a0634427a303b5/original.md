```
MultiHeadedBranch(covariate_idx, neurons, heads; activation, init_bias).
```

Convenience function for creating branches in Lux models. Constructs a neural  network containing a single hidden layer connecting to multiple independent  layers in parallel specified by `heads`. This way, the covariate effect shares a  similar base, but can still learn independent effects for each head. All hidden  layers contain the same number of `neurons`. It is advisable to use at most 2  covariates as input to the model to facilitate interpretation.

# Arguments:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: Index of the covariate(s) to use in the branch.
  * `neurons::Int`: The amount of neurons in the hidden layer.
  * `heads::Int`: The number of independent heads.
  * `activation`: Activation function to use in the hidden layer. Default = swish.
  * `init_bias`: Initialization function of the bias parameters. Default = ones32. Can help with improving the initial estimates.
