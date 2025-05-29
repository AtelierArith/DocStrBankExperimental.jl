```
SampleDataTable(analytetype::TypeOrFn, samplecol::Symbol, table; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(table, analytetype::TypeOrFn, samplecol::Symbol; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(samplecol::Symbol, table; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(table, samplecol::Symbol; analytename = setdiff(propertynames(table), [samplecol]))
```

Higher level interfaces for `SampleDataTable{A}`.

  * `analytename`: `AbstractVector`, the column names of `table` that are analyte names. It will be converted to `AbstractVector{String}` before conversion to `AbstractVector{A}` (`string.(analytename)`).
  * `samplecol`: `Symbol`, the column name that each element is sample name.
  * `analytetype`: type `A` or a function. After first conversion of `analytename`, it convert `analytename` to `AbstractVector{A}` using `cqamap(analytetype, analytename)`. See `cqaconvert` for the requirement of `analytetype`.
