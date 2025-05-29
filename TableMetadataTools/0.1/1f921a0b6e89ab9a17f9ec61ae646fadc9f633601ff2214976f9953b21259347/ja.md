```
note!(table, note; append::Bool=false)
```

`note`の文字列表現を`table`の`"note"`キーの値として保存し、`Tables.jl`テーブルインターフェースと互換性のある`:note`スタイルのメタデータとして保存します。

`append=true`の場合、既存の`"note"`メタデータを置き換えるのではなく、渡された`note`文字列を以前のメタデータに改行を追加して追加します。

参照: [`note`](@ref)
