```julia
PrintEuropeanMonth(year::DPart, month::DPart, io=stdout)
```

Print a calendar for the given European month as a markdown table to `io`.

For example:

```julia
julia> PrintEuropeanMonth(2022, 2)
```
