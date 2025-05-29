```
Log(; dtype::Maybe{Type} = nothing, base::StorageReal = e, eps::StorageReal = 0)
```

Element-wise operation that converts every element to its logarithm.

**Parameters**:

`dtype` - The default output data type is the [`float_dtype_for`](@ref) of the input data type.

`base` - The base of the logarithm. By default uses `e` (that is, computes the natural logarithm), which isn't convenient, but is the standard.

`eps` - Added to the input before computing the logarithm, to handle zero input data. By default is zero.
