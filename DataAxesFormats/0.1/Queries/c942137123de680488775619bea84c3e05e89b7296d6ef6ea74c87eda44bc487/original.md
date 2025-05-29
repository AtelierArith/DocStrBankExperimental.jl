```
Lookup(property::AbstractString) <: Query
```

A query operation for looking up the value of a property with some name. In a string [`Query`](@ref), this is specified using the `:` operator, followed by the property name to look up.

  * If the query state is empty, this looks up the value of a scalar property (e.g., `: version`).
  * If the query state contains a single axis, this looks up the value of a vector property (e.g., `/ cell : batch`).
  * If the query state contains two axes, this looks up the value of a matrix property (e.g., `/ cell / gene : UMIs`).

If the property does not exist, this is an error, unless this is followed by [`IfMissing`](@ref) (e.g., `: version || 1.0`).

If any of the axes has a single entry selected using [`IsEqual`](@ref), this will reduce the dimension of the result (e.g., `/ cell / gene = FOX1 : UMIs` is a vector, and both `/ cell = C1 / gene = FOX1 : UMIs` and `/ gene = FOX1 : is_marker` are scalars).

!!! note
    This, [`Names`](@ref) and [`Axis`](@ref) are the only [`QueryOperation`](@ref)s that also works as a complete [`Query`](@ref).

