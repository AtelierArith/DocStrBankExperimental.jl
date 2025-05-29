```
DataMatrix(matrix, var, obs; kwargs...)
```

Create a `DataMatrix` with the given `matrix`, `var` and `obs`.

The first column of `var`/`obs` are used as IDs.

Kwargs:

  * `duplicate_var` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate var IDs are found.
  * `duplicate_obs` - Set to `:ignore`, `:warn` or `:error` to decide what happens if duplicate obs IDs are found.
