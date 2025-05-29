```
rowselection(dt::DataTable, idcolumn::Union{String, Symbol}, regex::Regex, cols = Colon())
```

正規表現に基づいてテーブル選択を構築します。

```julia
rowselection(t, "b", r"hello|World")
```
