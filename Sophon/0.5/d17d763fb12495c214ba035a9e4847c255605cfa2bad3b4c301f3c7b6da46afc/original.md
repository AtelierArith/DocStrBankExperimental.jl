```
FactorizedDense(in_dims::Int, out_dims::Int, activation=identity;
                     mean::AbstractFloat=1.0f0, std::AbstractFloat=0.1f0,
                     init_weight=kaiming_uniform(activation), init_bias=zeros32)
```

Create a `Dense` layer where the weight is factorized into twa parts, the scaling factors for each row and the weight matrix.

## Arguments

  * `in_dims`: number of input dimensions
  * `out_dims`: number of output dimensions
  * `activation`: activation function

## Keyword Arguments

  * `mean`: mean of the scaling factors
  * `std`: standard deviation of the scaling factors
  * `init_weight`: weight initialization function
  * `init_bias`: bias initialization function

## Input

  * `x`: input vector or matrix

## Returns

  * `y = activation.(scale * weight * x+ bias)`.
  * Empty `NamedTuple()`.

## Parameters

  * `scale`: scaling factors. Shape: `(out_dims, 1)`
  * `weight`: Weight Matrix of size `(out_dims, in_dims)`.
  * `bias`: Bias of size `(out_dims, 1)`.

## References

[wang2022random](@cite)
