```
AnalysisTable(keys::AbstractVector{Symbol}, tables::AbstractVector{<: AbstractDataTable{A, S}})
```

A `Dictionary`-like constructor for `AnalysisTable` from two iterable inputs `keys` and `tables`. The first value of `keys` will be the index for the first value of `tables`.
