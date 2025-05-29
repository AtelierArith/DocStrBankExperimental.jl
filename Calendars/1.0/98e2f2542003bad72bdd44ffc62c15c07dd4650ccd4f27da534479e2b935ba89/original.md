```julia
SaveEuropeanMonth(year::DPart, month::DPart, dirname:String)
```

Save the calendar of the given European month as a markdown table to a file in the directory `dirname`. If no directory is given the file is written to the execution directory.

For example:

```julia
julia> SaveEuropeanMonth(2022, 2)
```
