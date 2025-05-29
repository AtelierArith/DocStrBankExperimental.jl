```
DimensionError <: Exception
DimensionError(name, dim_expected, dim_found)
```

Error for unexpected dimension. Output: "DimensionError: Input `name` should have length `dim_expected` not `dim_found`"
