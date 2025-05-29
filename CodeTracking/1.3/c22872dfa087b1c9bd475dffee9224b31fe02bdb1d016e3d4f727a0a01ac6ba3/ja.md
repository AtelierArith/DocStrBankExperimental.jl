```
filepath, line = whereis(lineinfo, method::Method)
```

特定のステートメントに関連付けられたファイルと行番号を返します `method`。 `lineinfo.line` には、`method` がコンパイルされた時点でのステートメントの行番号が含まれている必要があります。現在の位置が返されます。
