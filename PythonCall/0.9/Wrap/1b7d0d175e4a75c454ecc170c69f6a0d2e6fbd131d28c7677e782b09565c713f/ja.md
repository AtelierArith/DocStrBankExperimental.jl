```
PyPandasDataFrame(x; [indexname::Union{Nothing,Symbol}], [columnnames::Function], [columntypes::Function])
```

pandas DataFrame `x` を Tables.jl 互換のテーブルとしてラップします。

  * `indexname`: インデックスを含む列の名前。デフォルトは `nothing` で、インデックスを除外することを意味します。
  * `columnnames`: Python の列名（`Py`）を Julia の列名（`Symbol`）にマッピングする関数。デフォルトは `x -> Symbol(x)` です。
  * `columntypes`: 列名（`Symbol`）を受け取り、列の希望する要素型を返す関数、または自動推論を示すために `nothing` を返します。
