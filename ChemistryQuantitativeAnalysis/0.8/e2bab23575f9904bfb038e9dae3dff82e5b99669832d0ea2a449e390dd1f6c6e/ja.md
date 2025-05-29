```
AnalyteDataTable(analytecol::Symbol, sampletype::TypeOrFn, table; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(table, analytecol::Symbol, sampletype::TypeOrFn; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(analytecol::Symbol, table; samplename = setdiff(propertynames(table), [analytecol]))
AnalyteDataTable(table, analytecol::Symbol; samplename = setdiff(propertynames(table), [analytecol]))
```

`AnalyteDataTable{A, S}`の高レベルインターフェース。

  * `analytecol`: `Symbol`、各要素が分析物名である列名。
  * `samplename`: `AbstractVector`、`table`のサンプル名の列名。`AbstractVector{S}`に変換する前に`Vector{String}`に変換されます（`string.(samplename)`）。
  * `sampletype`: 型`S`または関数。最初の`sampletype`の変換の後、`samplename`を`AbstractVector{S}`に変換するために`cqamap(sampletype, sampletype)`を使用します。`sampletype`の要件については`cqaconvert`を参照してください。
