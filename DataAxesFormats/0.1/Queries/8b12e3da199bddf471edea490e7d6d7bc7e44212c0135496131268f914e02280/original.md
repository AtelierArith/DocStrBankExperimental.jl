```
Or(property::AbstractString) <: QueryOperation
```

A query operation for expanding the set of entries of an [`Axis`](@ref). In a string [`Query`](@ref), this is specified using the `|` operator, followed by the name of an axis property to look up to compute the mask.

This works similarly to [`And`](@ref), except that it adds to the mask (e.g., `/ gene & is_marker | is_noisy` will restrict the result vector to either marker or noisy genes).
