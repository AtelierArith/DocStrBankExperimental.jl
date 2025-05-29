```
readplist(stream::IO) -> Dict
readplist(filename::AbstractString) -> Dict
```

`filename`という名前のファイルから、または以前に開いた`IO`ストリームオブジェクトからNeXTSTEPスタイルのPListを読み取ります。これはファイル、文字列、またはソケットからのものである可能性があります。いずれの場合も、辞書が返されます。
