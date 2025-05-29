```
StdN(; dtype::Maybe{Type} = nothing, eps::StorageReal = 0)
```

Reduction operation that returns the (uncorrected) standard deviation of the values, normalized (divided) by the mean value.

**Parameters**

`dtype` - The default output data type is the [`float_dtype_for`](@ref) of the input data type.

`eps` - Added to the mean before computing the division, to handle zero input data. By default is zero.
