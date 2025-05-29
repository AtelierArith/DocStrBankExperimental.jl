```
IfMissing(value::StorageScalar; dtype::Maybe{Type} = nothing) <: QueryOperation
```

A query operation providing a value to use if the data is missing some property. In a string [`Query`](@ref), this is specified using the `||` operator, followed by the value to use, and optionally followed by the data type of the value (e.g., `: score || 1 Float32`).

If the data type is not specified, and the `value` isa `AbstractString`, then the data type is deduced using [`guess_typed_value`](@ref) of the `value`.
