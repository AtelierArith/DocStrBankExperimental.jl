```
note(table, column)
```

Return string representation of the value of the `"note"` column-level metadata for column `column` in `table` that must be compatible with Tables.jl table interface.

If `"note"` column-level metadata for column `column` is missing return "".

See also: [`note!`](@ref) ```
