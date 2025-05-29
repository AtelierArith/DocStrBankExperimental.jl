```
AdaptiveMaxPool(output_size)
```

Adaptive Max Pooling layer. Calculates the necessary window size such that its output has `size(y)[1:N] == output_size`.

## Arguments

  * `output_size`: Size of the first `N` dimensions for the output

## Inputs

  * `x`: Expects as input an array with `ndims(x) == N + 2`, i.e. channel and batch dimensions, after the `N` feature dimensions, where `N = length(output_size)`.

## Returns

  * Output of size `(out..., C, N)`
  * Empty `NamedTuple()`
