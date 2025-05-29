```
Scale(dims, activation=identity; init_weight=ones32, init_bias=zeros32, use_bias=True())
```

Create a Sparsely Connected Layer with a very specific structure (only Diagonal Elements are non-zero). The forward pass is given by: `y = activation.(weight .* x .+ bias)`

## Arguments

  * `dims`: size of the learnable scale and bias parameters.
  * `activation`: activation function

## Keyword Arguments

  * `init_weight`: initializer for the weight matrix (`weight = init_weight(rng, out_dims, in_dims)`)
  * `init_bias`: initializer for the bias vector (ignored if `use_bias=false`)
  * `use_bias`: Trainable bias can be disabled entirely by setting this to `false`

## Input

  * `x` must be an Array of size `(dims..., B)` or `(dims...[0], ..., dims[k])` for `k ≤ size(dims)`

## Returns

  * Array of size `(dims..., B)` or `(dims...[0], ..., dims[k])` for `k ≤ size(dims)`
  * Empty `NamedTuple()`

## Parameters

  * `weight`: Weight Array of size `(dims...)`
  * `bias`: Bias of size `(dims...)`
