```
write_table!(filename:: AbstractString, table; kwargs...):: AbstractString
```

`filename`: path and filename of the output file `table`: a Tables.jl compatible object (e.g. a DataFrame) for storage `kwargs...`: keyword arguments passed to the underlying file writing function (e.g. `CSV.write`)

Example:

```
write_table!("my_output.csv", df)
```
