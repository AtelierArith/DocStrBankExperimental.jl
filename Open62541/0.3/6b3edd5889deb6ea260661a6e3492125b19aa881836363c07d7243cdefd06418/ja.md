```
UInt64_clear(x::Ptr{UInt64})
```

は、オブジェクト `x` の動的に割り当てられた内容を削除し、`UInt64_init(x)` を呼び出して型とそのメモリをリセットします。
