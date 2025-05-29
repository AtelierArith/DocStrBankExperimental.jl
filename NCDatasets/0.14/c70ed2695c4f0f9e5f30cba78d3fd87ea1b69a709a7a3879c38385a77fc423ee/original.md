```
a = nomissing(da)
```

Return the values of the array `da` of type `Array{Union{T,Missing},N}` (potentially containing missing values) as a regular Julia array `a` of the same element type. It raises an error if the array contains at least one missing value.
