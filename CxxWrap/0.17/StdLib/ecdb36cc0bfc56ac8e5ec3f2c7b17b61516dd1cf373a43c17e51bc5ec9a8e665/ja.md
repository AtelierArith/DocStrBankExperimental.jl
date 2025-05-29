```
StdString(str::String)
```

文字列の内容から `StdString` を作成します。すべてのヌル文字 ('\0') は文字列に含まれ、`ncodeunits(str) == ncodeunits(StdString(str))` となります。
