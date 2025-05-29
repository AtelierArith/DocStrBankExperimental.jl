```
note!(table, column note; append::Bool=false)
```

`table`内の`column`に対して、`:note`スタイルの列レベルメタデータとして、`note`の文字列表現を`"note"`キーの値として保存します。この`table`はTables.jlのテーブルインターフェースと互換性がある必要があります。

`append=true`の場合、既存の`"note"`メタデータを置き換えるのではなく、渡された`note`文字列を以前のメタデータに改行を追加した後に追加します。

参照: [`note`](@ref)
