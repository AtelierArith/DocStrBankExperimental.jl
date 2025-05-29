```
AnalyteDataTable(analytecol::Symbol, sampletype::TypeOrFn, table; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(table, analytecol::Symbol, sampletype::TypeOrFn; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(analytecol::Symbol, table; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(table, analytecol::Symbol; samplename = setdiff(propertynames(table), [analytecol]))
```

Higher level interfaces for `AnalyteDataTable{A, S}`.

  * `analytecol`: `Symbol`, the column name that each element is analyte name.
  * `samplename`: `AbstractVector`, the column names of `table` that are sample names. It will be converted to `Vector{String}` before conversion to `AbstractVector{S}` (`string.(samplename)`).
  * `sampletype`: type `S` or a function. After first conversion of `sampletype`, it converts `samplename` to `AbstractVector{S}` using `cqamap(sampletype, sampletype)`. See `cqaconvert` for the requirement of `sampletype`.
