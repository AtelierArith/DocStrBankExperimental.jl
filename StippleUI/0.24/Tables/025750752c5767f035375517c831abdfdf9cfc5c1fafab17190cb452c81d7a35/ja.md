```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, f::Function, cols = Colon())
```

関数に基づいてテーブル選択を構築します。

```
rowselection(dt, "a", iseven)
rowselection(dt, "a", x -> x > 3)
```
