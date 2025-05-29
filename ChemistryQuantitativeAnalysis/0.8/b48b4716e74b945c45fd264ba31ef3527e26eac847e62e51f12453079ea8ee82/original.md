```
SampleDataTable(tbl::AnalyteDataTable{A, S, N, T}, samplecol::Symbol, tablesink::TypeOrFn = T)
SampleDataTable(samplecol::Symbol, tablesink::TypeOrFn, tbl::AnalyteDataTable)
SampleDataTable(samplecol::Symbol, tbl::AnalyteDataTable)
```

Convert `AnalyteDataTable` to `SampleDataTable` with `samplecol` as the column name of sample.
