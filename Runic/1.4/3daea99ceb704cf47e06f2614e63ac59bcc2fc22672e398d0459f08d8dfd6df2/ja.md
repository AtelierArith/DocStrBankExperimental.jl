```
Runic.format_file(
    inputfile::AbstractString, outputfile::AbstractString = inputfile;
    inplace::Bool=false,
)
```

ファイル `inputfile` をフォーマットし、フォーマットされたテキストを `outputfile` に書き込みます。

`inputfile` と `outputfile` が同じファイルである場合、キーワード引数 `inplace = true` を設定する必要があります。
