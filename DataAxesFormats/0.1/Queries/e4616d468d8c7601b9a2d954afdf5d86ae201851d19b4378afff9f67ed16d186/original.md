```
Names(kind::Maybe{AbstractString} = nothing) <: Query
```

A query operation for looking up a set of names. In a string [`Query`](@ref), this is specified using the `?` operator, optionally followed by the kind of objects to name.

  * If the query state is empty, a `kind` must be specified, one of `scalars` or `axes`, and the result is the set of their names (`? scalars`, `? axes`).
  * If the query state contains a single axis (without any masks), the `kind` must not be specified, and the result is the set of names of vector properties of the axis (e.g., `/ cell ?`).
  * If the query state contains two axes (without any masks), the `kind` must not be specified, and the result is the set of names of matrix properties of the axes (e.g., `/ cell / gene ?`).

!!! note
    This, [`Lookup`](@ref) and [`Axis`](@ref) are the only [`QueryOperation`](@ref)s that also works as a complete [`Query`](@ref).

