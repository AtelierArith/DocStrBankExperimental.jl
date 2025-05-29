```
isrelocatable(oh::ObjectHandle)
```

与えられた `ObjectHandle` が再配置可能なオブジェクトファイルを表す場合、`true` を返します。例えば、`gcc -c` によって生成された `.o` ファイルなどです。
