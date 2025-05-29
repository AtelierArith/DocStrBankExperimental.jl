```
@reverse_range expr
```

rewrites range expression `expr` with extended syntax. The result is an `Int`-valued index range (possibly Cartesian) where indices are running in the reverse direction (with a negative step). Call [`@range`](@ref) if a positive step is required and see the documentation of this macro for more explanations.

See [`EasyRanges.normalize`](@ref) to implement non-standard index or range types in the [`@range`](@ref) and `@reverse_range` macros.
