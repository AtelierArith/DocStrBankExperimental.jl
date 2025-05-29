```
IsLess(value::StorageScalar) <: QueryOperation
```

A query operation for converting a vector value to a Boolean mask by comparing it some value. In a string [`Query`](@ref), this is specified using the `<` operator, followed by the value to compare with.

A string value is automatically converted into the same type as the vector values (e.g., `/ cell & probability < 0.5` will restrict the result vector only to cells whose probability is less than half).
