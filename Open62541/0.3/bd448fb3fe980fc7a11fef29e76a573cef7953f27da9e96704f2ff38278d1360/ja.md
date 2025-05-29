```
UInt32_deleteMembers(x::Ptr{UInt32})
```

（非推奨、代わりに `UInt32_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`UInt32_init(x)` を呼び出して型とそのメモリをリセットします。
