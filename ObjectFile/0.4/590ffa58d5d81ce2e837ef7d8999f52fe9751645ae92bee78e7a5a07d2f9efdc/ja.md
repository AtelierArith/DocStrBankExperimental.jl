```
find_library(oh::ObjectHandle, soname::String)
```

指定された `soname` の絶対パスを返します。これは、指定された `ObjectHandle` が実行時に使用するリンカの検索パスを使用します。詳細については、`find_library(::RPath, ::String)` のドキュメントを参照してください。
