```
Dense(in_dims => out_dims, activation=identity; init_weight=nothing,
      init_bias=nothing, use_bias=True())
```

Create a traditional fully connected layer, whose forward pass is given by: `y = activation.(weight * x .+ bias)`

## Arguments

  * `in_dims`: number of input dimensions
  * `out_dims`: number of output dimensions
  * `activation`: activation function

## Keyword Arguments

  * `init_weight`: initializer for the weight matrix (`weight = init_weight(rng, out_dims, in_dims)`). If `nothing`, then we use [`kaiming_uniform`](@ref) with gain computed on the basis of the activation function (taken from Pytorch [`nn.init.calculate_gain`](https://pytorch.org/docs/stable/nn.init.html#torch.nn.init.calculate_gain)).
  * `init_bias`: initializer for the bias vector (ignored if `use_bias=false`). If `nothing`, then we use uniform distribution with bounds `-bound` and `bound` where `bound = inv(sqrt(in_dims))`.
  * `use_bias`: Trainable bias can be disabled entirely by setting this to `false`

## Input

  * `x` must be an AbstractArray with `size(x, 1) == in_dims`

## Returns

  * AbstractArray with dimensions `(out_dims, ...)` where `...` are the dimensions of `x`
  * Empty `NamedTuple()`

## Parameters

  * `weight`: Weight Matrix of size `(out_dims, in_dims)`
  * `bias`: Bias of size `(out_dims, 1)` (present if `use_bias=true`)
