```
IsEqual(value::StorageScalar) <: QueryOperation
```

Equality is used for two purposes:

  * As a comparison operator, similar to [`IsLess`](@ref) except that uses `=` instead of `<` for the comparison.
  * To select a single entry from a vector. This allows a query to select a single scalar from a vector (e.g., `/ gene = FOX1 : is_marker`) or from a matrix (e.g., `/ cell = ATCG / gene = FOX1 : UMIs`); or to slice a single vector from a matrix (e.g., `/ cell = ATCG / gene : UMIs` or `/ cell / gene = FOX1 : UMIs`).
