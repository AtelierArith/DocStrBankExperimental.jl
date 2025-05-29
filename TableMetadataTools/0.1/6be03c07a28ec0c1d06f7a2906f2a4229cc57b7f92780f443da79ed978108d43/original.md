```
label(table, column)
```

Return string representation of the value of the `"label"` column-level metadata of column `column` in `table` that must be compatible with Tables.jl table interface.

If `"label"` column-level metadata for column `column` is missing return name of column `column` as string.

See also: [`label!`](@ref), [`labels`](@ref) ```
