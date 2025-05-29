```
ReadStatTable(table::ReadStatTable, ext::AbstractString; kwargs...)
```

既存の `ReadStatTable` から、拡張子 `ext` のサポートされているファイル形式の `ReadStatTable` を構築します。

# キーワード

  * `update_width::Bool = true`: 既存のメタデータ値ではなく、実際のデータ列を確認することによって、各文字列変数のストレージ幅を決定します。
