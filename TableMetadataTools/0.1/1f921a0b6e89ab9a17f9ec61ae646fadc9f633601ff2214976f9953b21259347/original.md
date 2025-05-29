```
note!(table, note; append::Bool=false)
```

Store string representation of `note` as value of `"note"` key with `:note`-style as table-level metadata in `table` that must be compatible with Tables.jl table interface.

If `append=true` then instead of replacing existing `"note"` metadata append the passed `note` string to the previously present metadata after adding a newline.

See also: [`note`](@ref)
