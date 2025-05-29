```julia
PrintIsoWeek(year::DPart, week::DPart, io=stdout)
```

Print a calendar for the given Iso week as a markdown table to `io`.

For example:

```julia
julia> PrintIsoWeek(2022, 2)
```
