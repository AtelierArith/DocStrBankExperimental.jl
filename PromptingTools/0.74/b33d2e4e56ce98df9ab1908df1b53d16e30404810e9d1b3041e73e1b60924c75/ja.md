```
pprint(io::IO, msg::AbstractMessage; text_width::Int = displaysize(io)[2])
```

与えられた IO ストリームに単一の `AbstractMessage` をきれいに表示します。

`text_width` は表示されるテキストの幅です。指定されていない場合、与えられた IO ストリームの幅にデフォルト設定され、必要に応じて `newline` 区切りが追加されます。
