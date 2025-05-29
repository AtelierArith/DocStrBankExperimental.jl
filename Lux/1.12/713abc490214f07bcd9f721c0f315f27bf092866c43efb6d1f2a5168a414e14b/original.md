```
Bilinear((in1_dims, in2_dims) => out, activation=identity; init_weight=nothing,
         init_bias=nothing, use_bias=True())
Bilinear(in12_dims => out, activation=identity; init_weight=nothing,
         init_bias=nothing, use_bias=True())
```

Create a fully connected layer between two inputs and an output, and otherwise similar to [`Dense`](@ref). Its output, given vectors `x` & `y`, is another vector `z` with, for all `i in 1:out`:

`z[i] = activation(x' * W[i, :, :] * y + bias[i])`

If `x` and `y` are matrices, then each column of the output `z = B(x, y)` is of this form, with `B` the Bilinear layer.

## Arguments

  * `in1_dims`: number of input dimensions of `x`
  * `in2_dims`: number of input dimensions of `y`
  * `in12_dims`: If specified, then `in1_dims = in2_dims = in12_dims`
  * `out`: number of output dimensions
  * `activation`: activation function

## Keyword Arguments

  * `init_weight`: initializer for the weight matrix (`weight = init_weight(rng, out_dims, in1_dims, in2_dims)`). If `nothing`, then we use uniform distribution with bounds `-bound` and `bound` where `bound = inv(sqrt(in1_dims))`.
  * `init_bias`: initializer for the bias vector (ignored if `use_bias=false`). If `nothing`, then we use uniform distribution with bounds `-bound` and `bound` where `bound = inv(sqrt(in1_dims))`.
  * `use_bias`: Trainable bias can be disabled entirely by setting this to `false`

## Input

  * A 2-Tuple containing

      * `x` must be an AbstractArray with `size(x, 1) == in1_dims`
      * `y` must be an AbstractArray with `size(y, 1) == in2_dims`
  * If the input is an AbstractArray, then `x = y`

## Returns

  * AbstractArray with dimensions `(out_dims, size(x, 2))`
  * Empty `NamedTuple()`

## Parameters

  * `weight`: Weight Matrix of size `(out_dims, in1_dims, in2_dims)`
  * `bias`: Bias of size `(out_dims, 1)` (present if `use_bias=true`)
