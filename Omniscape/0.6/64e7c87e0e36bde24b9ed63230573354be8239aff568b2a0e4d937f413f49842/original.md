```
missing_array_to_array(A::MissingArray{T, N}, nodata::Number)
```

This function converts an array of type `MissingArray` to a numeric array  and replaces `missing` entries with `nodata`. `MissingArray{T, N}` is an alias  for `Array{Union{T, Missing}, N}`.

# Parameters

**`A`**: The array to convert.

**`nodata`**: The numeric value with which `missing` values will be replaced in  the result.
