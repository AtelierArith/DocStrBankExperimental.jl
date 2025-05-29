```
UInt8_deleteMembers(x::Ptr{UInt8})
```

（非推奨、代わりに `UInt8_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`UInt8_init(x)` を呼び出して型とそのメモリをリセットします。
