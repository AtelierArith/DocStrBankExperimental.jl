```
Quantile(; dtype::Maybe{Type} = nothing, p::StorageReal)
```

Reduction operation that returns the quantile value, that is, a value such that a certain fraction of the values is lower.

**Parameters**

`dtype` - The default output data type is the [`float_dtype_for`](@ref) of the input data type.

`p` - The fraction of values below the result (e.g., the 0 computes the minimum, the 0.5 computes the median, and 1.0 computes the maximum). There's no default.
