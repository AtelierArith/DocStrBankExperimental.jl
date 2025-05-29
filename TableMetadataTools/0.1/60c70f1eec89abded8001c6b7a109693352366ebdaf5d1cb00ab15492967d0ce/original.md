```
label!(table, column, label)
```

Store string representation of `label` as value of `"label"` key with `:note`-style as column-level metadata for column `column` in `table` that must be compatible with Tables.jl table interface.

See also: [`label`](@ref), [`labels`](@ref)
