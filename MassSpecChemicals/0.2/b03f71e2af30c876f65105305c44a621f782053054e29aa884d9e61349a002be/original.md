```
chemicalabbr(chemical::AbstractChemical; kwargs...)
```

Get abbreviation of `chemical`. It is equivalent to `getchemicalattr(chemical, :abbreviation; kwargs...)` except that it returns `chemicalname(chemical; kwargs...)` when abbreviation is not available.
