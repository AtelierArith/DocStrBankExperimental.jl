```
log_row(vals)
```

Creates a table row from the values on `vals` according to their types. Pass the names and types of `vals` to [`log_header`](@ref) for a logging table. Uses internal formatting specification given by `SolverCore.formats`.

To handle a missing value, add the type instead of the number:

```
@info log_row(Any[1.0, 1])
@info log_row(Any[Float64, Int])
```

Prints

```
[ Info:  1.0e+00       1
[ Info:        -       -
```

Keyword arguments:

  * `colsep::Int`: Number of spaces between columns (Default: 2)
