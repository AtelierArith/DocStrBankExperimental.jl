```
last(df::AbstractDataFrame, n::Integer; view::Bool=false)
```

`df`の最後の`n`行を持つデータフレームを取得します。`n`が`df`の行数より大きい場合はすべての行を取得します。`n`が負の場合はエラーになります。

`view=false`の場合は、新しく割り当てられた`DataFrame`が返されます。`view=true`の場合は、`df`への`SubDataFrame`ビューが返されます。

メタデータ: この関数は、テーブルレベルおよびカラムレベルの`:note`スタイルのメタデータを保持します。
