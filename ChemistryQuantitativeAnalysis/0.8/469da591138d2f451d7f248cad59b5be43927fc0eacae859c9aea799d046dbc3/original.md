```
AnalyteDataTable(tbl::SampleDataTable{A, S, N, T}, analytecol::Symbol, tablesink::TypeOrFn = T)
AnalyteDataTable(analytecol::Symbol, tablesink::TypeOrFn, tbl::SampleDataTable)
AnalyteDataTable(analytecol::Symbol, tbl::SampleDataTable)
```

Convert `SampleDataTable` to `AnalyteDataTable` with `analytecol` as the column name of analyte.
