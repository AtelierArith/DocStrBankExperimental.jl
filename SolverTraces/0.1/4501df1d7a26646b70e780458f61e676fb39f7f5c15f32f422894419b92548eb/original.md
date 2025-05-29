```
ScalarColumn(n::R, header[, signed=false]) where {R<:Real}
```

Construct a [`ScalarColumn`](@ref) for the scalar value `n`, with a format automatically generated depending on `R` is an integer or not, and whether it can be signed.
