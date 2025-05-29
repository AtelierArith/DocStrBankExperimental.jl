```
execute([restype=StructArray], tap::TAPService, query::AbstractString; kwargs...)
```

Execute the ADQL `query` at the specified TAP service, and return the result as a `StructArray` - a fully featured Julia table.

`kwargs` are passed to `VOTables.read`, for example specify `unitful=true` to parse columns with units into `Unitful.jl` values.
