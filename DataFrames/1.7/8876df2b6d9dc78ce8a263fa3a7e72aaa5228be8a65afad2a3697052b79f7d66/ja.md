```
first(df::AbstractDataFrame, n::Integer; view::Bool=false)
```

データフレーム `df` の最初の `n` 行を取得します。`n` が `df` の行数より大きい場合はすべての行を取得します。`n` が負の場合はエラーになります。

`view=false` の場合は、新しく割り当てられた `DataFrame` が返されます。`view=true` の場合は、`df` への `SubDataFrame` ビューが返されます。

メタデータ: この関数は、テーブルレベルおよびカラムレベルの `:note` スタイルのメタデータを保持します。
