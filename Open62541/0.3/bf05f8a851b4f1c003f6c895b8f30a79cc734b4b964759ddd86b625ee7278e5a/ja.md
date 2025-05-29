```
UInt64_deleteMembers(x::Ptr{UInt64})
```

（非推奨、代わりに `UInt64_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`UInt64_init(x)` を呼び出して型とそのメモリをリセットします。
