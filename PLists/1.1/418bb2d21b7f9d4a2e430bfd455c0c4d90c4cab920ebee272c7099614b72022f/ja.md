```
 writeplist(stream::IO, obj)
 writeplist(filename::AbstractString, obj)
```

NeXTSTEPプロパティリスト形式を使用して、IO `stream`または`filename`という名前のファイルにオブジェクトを書き込みます。`obj`は辞書、数値、または文字列である可能性があります。
