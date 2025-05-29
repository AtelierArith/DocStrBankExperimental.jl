```
compose(table, colnames; keepcols=true, as=:coda)
```

Convert columns `colnames` of `table` into parts of a composition and save the result in a [`CoDaArray`](@ref). If `keepcols` is set to `true`, then save the result `as` a column in a new table with all other columns preserved.
