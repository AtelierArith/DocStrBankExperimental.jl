```
GeoMean(; dtype::Maybe{Type} = nothing, eps::StorageReal = 0.0)
```

Reduction operation that returns the geometric mean value.

**Parameters**

`dtype` - The default output data type is the [`float_dtype_for`](@ref) of the input data type.

`eps` - The regularization factor added to each value and subtracted from the raw geo-mean, to deal with zero values.
