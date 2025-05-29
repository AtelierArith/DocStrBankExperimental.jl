```
LPPool(window; stride=window, pad=0, dilation=1, p=2)
```

LP Pooling layer, which replaces all pixels in a block of size `window` with the reduction operation: lp.

## Arguments

  * `window`: Tuple of integers specifying the size of the window. Eg, for 2D pooling `length(window) == 2`

## Keyword Arguments

  * `stride`: Should each be either single integer, or a tuple with `N` integers
  * `dilation`: Should each be either single integer, or a tuple with `N` integers
  * `pad`: Specifies the number of elements added to the borders of the data array. It can be

      * a single integer for equal padding all around,
      * a tuple of `N` integers, to apply the same padding at begin/end of each spatial dimension,
      * a tuple of `2*N` integers, for asymmetric padding, or
      * the singleton `SamePad()`, to calculate padding such that `size(output,d) == size(x,d) / stride` (possibly rounded) for each spatial dimension.

!!! danger "GPU Support"
    This layer is currently only supported on CPU.


# Extended Help

## Inputs

  * `x`: Data satisfying `ndims(x) == N + 2`, i.e. `size(x) = (I_N, ..., I_1, C, N)`

## Returns

  * Output of the pooling `y` of size `(O_N, ..., O_1, C, N)` where

$$
    O_i = \left\lfloor\frac{I_i + p_i + p_{(i + N) \% |p|} - d_i \times (k_i - 1)}{s_i} + 1\right\rfloor
$$

  * Empty `NamedTuple()`
