```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, values, cols = Colon())
```

インデックスと値/値のリストに基づいてテーブル選択を構築します。

```
rowselection(dt, "a", [1, 3])
rowselection(dt, "a", 2:9)
```
