```
SampleDataTable(tbl::SampleDataTable{A, S, N, T}, samplecol::Symbol, tablesink::TypeOrFn = T)
SampleDataTable(samplecol::Symbol, tablesink::TypeOrFn, tbl::SampleDataTable)
SampleDataTable(samplecol::Symbol, tbl::SampleDataTable)
```

`samplecol`をサンプルの列名として、`AnalyteDataTable`を`SampleDataTable`に変換します。
