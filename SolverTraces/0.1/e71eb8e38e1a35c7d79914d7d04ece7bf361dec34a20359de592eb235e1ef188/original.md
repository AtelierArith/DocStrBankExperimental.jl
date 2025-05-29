```
ScalarColumn(n, header, ::Type{R}[, signed=false]) where {R<:Real}
```

Construct a [`ScalarColumn`](@ref) for the callback function `n`, with a format automatically generated depending on `R` is an integer or not, and whether it can be signed.
