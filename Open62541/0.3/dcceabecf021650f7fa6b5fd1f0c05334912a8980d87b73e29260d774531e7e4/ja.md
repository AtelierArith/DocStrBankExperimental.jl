```
UInt16_deleteMembers(x::Ptr{UInt16})
```

（非推奨、代わりに `UInt16_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`UInt16_init(x)` を呼び出して型とそのメモリをリセットします。
