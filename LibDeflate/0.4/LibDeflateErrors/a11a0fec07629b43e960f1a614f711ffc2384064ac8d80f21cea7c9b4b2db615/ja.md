```
LibDeflateError
```

`UInt8` 列挙型で、LibDeflate がエラーに遭遇したことを示します。エラーの数値は非破壊的リリース間で安定していませんが、その名前は安定しています。特定のエラーをチェックするコードは、例えば `== LibDeflateErrors.gzip_not_deflate` のようにチェックするべきです。成功した操作は決して `LibDeflateError` を返しません。
