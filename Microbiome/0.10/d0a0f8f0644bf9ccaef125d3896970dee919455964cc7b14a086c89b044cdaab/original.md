```
rankfilter(comm::AbstractAbundanceTable, cl::Union{Symbol, Int}; keepempty=false)
```

Return a copy of `comm`, where only rows that have `taxrank(feature) == cl` are kept. Use `keepempty = true` to also keep features that don't have a `rank` (eg "UNIDENTIFIED").
