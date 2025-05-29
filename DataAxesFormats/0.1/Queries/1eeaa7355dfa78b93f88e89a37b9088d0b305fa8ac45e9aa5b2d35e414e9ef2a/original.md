```
XorNot(property::AbstractString) <: QueryOperation
```

Same as [`Xor`](@ref) but use the inverse of the mask. In a string [`Query`](@ref), this is specified using the `^!` operator, followed by the name of an axis property to look up to compute the mask.
