```
AnalyteDataTable(tbl::SampleDataTable{A, S, N, T}, analytecol::Symbol, tablesink::TypeOrFn = T)
AnalyteDataTable(analytecol::Symbol, tablesink::TypeOrFn, tbl::SampleDataTable)
AnalyteDataTable(analytecol::Symbol, tbl::SampleDataTable)
```

`SampleDataTable`を`AnalyteDataTable`に変換し、`analytecol`を分析物の列名として使用します。
