```
IfNot(value::Maybe{StorageScalar} = nothing) <: QueryOperation
```

A query operation providing a value to use for "false-ish" values in a vector (empty strings, zero numeric values, or false Boolean values). In a string [`Query`](@ref), this is indicated using the `??` operator, optionally followed by a value to use.

If the value is `nothing` (the default), then these entries are dropped (masked out) of the result (e.g., `/ cell : type ?` behaves the same as `/ cell & type : type`, that is, returns the type of the cells which have a non-empty type). Otherwise, this value is used instead of the "false-ish" value (e.g., `/ cell : type ? Outlier` will return a vector of the type of each cell, with the value `Outlier` for cells with an empty type). When fetching properties, this is the final value (e.g., `/ cell : type ? red => color` will return a vector of the color of the type of each cell, with a `red` color for the cells with an empty type).

If the `value` isa `AbstractString`, then it is automatically converted to the data type of the elements of the results vector.
