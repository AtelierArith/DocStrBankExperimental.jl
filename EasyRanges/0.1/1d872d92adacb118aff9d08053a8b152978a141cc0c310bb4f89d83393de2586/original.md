```
@range expr
```

rewrites range expression `expr` with extended syntax. The result is an `Int`-valued index range (possibly Cartesian) where indices are running in the forward direction (with a positive step). Call [`@reverse_range`](@ref) if a negative step is required.

Operations (`+`, `-`, `∩`, etc.) in `expr` shall only involve indices or index ranges. The syntax `$(subexpr)` may be used to protect any sub-expression `subexpr` of `expr` from being interpreted as a range expression.

See [`EasyRanges.normalize`](@ref) to implement non-standard index or range types in the `@range` and [`@reverse_range`](@ref) macros.
