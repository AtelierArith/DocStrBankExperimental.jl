```
SingleHeadedBranch(covariate_idx, neurons; activation, init_bias).
```

Convenience function for creating branches in Lux models. Constructs a single  hidden layer neural network with the specified number of `neurons`. It is advisable to use at most 2 covariates as input to the model to facilitate interpretation.

# Arguments:

  * `covariate_idx::Union{AbstractVector{<:Int}, Int}`: Index of the covariate(s) to use in the branch.
  * `neurons::Int`: The amount of neurons in the hidden layer.
  * `activation`: Activation function to use in the hidden layer. Default = swish.
  * `init_bias`: Initialization function of the bias parameters. Default = ones32. Can help with improving the initial estimates.
