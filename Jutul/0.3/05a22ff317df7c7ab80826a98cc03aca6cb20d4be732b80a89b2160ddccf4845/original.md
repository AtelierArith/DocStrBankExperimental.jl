```
get_diagonal_entries(eq::JutulEquation, eq_s)
```

Get the diagonal entries of a cache, i.e. the entries where entity type and index equals that of the governing equation.

Note: Be very careful about modifications to this array, as this is a view into the internal AD buffers and it is very easy to create inconsistent Jacobians.
