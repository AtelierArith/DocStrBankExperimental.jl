```
missingarray(A::Array{T, N}, T::DataType, nodata::Number)
```

This function converts an array to a `MissingArray` and replaces `nodata` values with `missing` in the output. `MissingArray{T, N}` is an alias  for `Array{Union{T, Missing}, N}`. This function can be used to prepare inputs for [`run_omniscape`](@ref).

# Parameters

**`A`**: The array to convert.

**`T`**: The data type for the output (e.g. Float64 or Float32).

**`nodata`**: The numeric value to be replaced by `missing` in the result.
