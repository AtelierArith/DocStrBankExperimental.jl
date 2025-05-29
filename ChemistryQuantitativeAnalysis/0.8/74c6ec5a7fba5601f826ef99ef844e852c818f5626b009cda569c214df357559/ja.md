```
SampleDataTable(analytetype::TypeOrFn, samplecol::Symbol, table; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(table, analytetype::TypeOrFn, samplecol::Symbol; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(samplecol::Symbol, table; analytename = setdiff(propertynames(table), [samplecol]))
SampleDataTable(table, samplecol::Symbol; analytename = setdiff(propertynames(table), [samplecol]))
```

`SampleDataTable{A}`の高レベルインターフェース。

  * `analytename`: `AbstractVector`、`table`の列名で、アナリート名です。`AbstractVector{A}`に変換する前に`AbstractVector{String}`に変換されます（`string.(analytename)`）。
  * `samplecol`: `Symbol`、各要素がサンプル名である列名です。
  * `analytetype`: 型`A`または関数です。最初の`analytename`の変換後、`analytename`を`cqamap(analytetype, analytename)`を使用して`AbstractVector{A}`に変換します。`analytetype`の要件については`cqaconvert`を参照してください。
