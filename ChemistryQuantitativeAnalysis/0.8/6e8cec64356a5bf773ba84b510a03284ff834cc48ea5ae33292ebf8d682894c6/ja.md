```
AnalysisTable(keys::AbstractVector{Symbol}, tables::AbstractVector{<: AbstractDataTable{A, S}})
```

`AnalysisTable`の`Dictionary`のようなコンストラクタで、2つの反復可能な入力`keys`と`tables`から作成されます。`keys`の最初の値は、`tables`の最初の値のインデックスになります。
