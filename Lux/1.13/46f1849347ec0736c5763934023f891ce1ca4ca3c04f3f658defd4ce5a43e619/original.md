```
GlobalLPPool(; p=2)
```

Global LP Pooling layer. Transforms `(w, h, c, b)`-shaped input into `(1, 1, c, b)`-shaped output, by performing mean pooling on the complete `(w, h)`-shaped feature maps.

!!! danger "GPU Support"
    This layer is currently only supported on CPU.


## Inputs

  * `x`: Data satisfying `ndims(x) > 2`, i.e. `size(x) = (I_N, ..., I_1, C, N)`

## Returns

  * Output of the pooling `y` of size `(1, ..., 1, C, N)`
  * Empty `NamedTuple()`
