```
Xor(property::AbstractString) <: QueryOperation
```

A query operation for flipping the set of entries of an [`Axis`](@ref). In a string [`Query`](@ref), this is specified using the `^` operator, followed by the name of an axis property to look up to compute the mask.

This works similarly to [`Or`](@ref), except that it flips entries in the mask (e.g., `/ gene & is_marker ^ is_noisy` will restrict the result vector to either marker or noisy genes, but not both).
