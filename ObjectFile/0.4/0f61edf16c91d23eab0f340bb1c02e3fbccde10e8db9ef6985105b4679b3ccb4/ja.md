```
read(oh::ObjectHandle, section::Section)
```

指定された `ObjectHandle` から `section` で参照されるセクションの内容を読み取り、`Vector{UInt8}` を返します。
