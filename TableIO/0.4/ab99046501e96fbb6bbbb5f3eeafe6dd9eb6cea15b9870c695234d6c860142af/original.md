```
read_table(filename:: AbstractString; kwargs...)
```

`filename`: path and filename of the input file `kwargs...`: keyword arguments passed to the underlying file reading function (e.g. `CSV.File`)

Returns a Tables.jl interface compatible object.

Example:

```
df = DataFrame(read_table("my_data.csv"); copycols=false)
```
