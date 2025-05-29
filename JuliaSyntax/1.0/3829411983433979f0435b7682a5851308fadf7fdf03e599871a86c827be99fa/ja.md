```
SourceFile(code [; filename=nothing, first_line=1, first_index=1])
```

関連するファイル名と行番号を持つUTF-8ソーステキストで、各行の開始位置の文字インデックスを保存します。 `first_line` と `first_index` を使用して、より大きなソーステキスト内の `code` の最初の文字の行番号とインデックスを指定できます。

`SourceFile` は `getindex` または `view` を介してインデックス指定され、文字列を取得できます。 バイトオフセットの行情報は、`source_line`、`source_location`、および `source_line_range` 関数を介して調べることができます。
