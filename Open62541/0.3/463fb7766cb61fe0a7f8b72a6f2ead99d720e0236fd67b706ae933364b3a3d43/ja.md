```
Int8_deleteMembers(x::Ptr{Int8})
```

（非推奨、代わりに `Int8_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`Int8_init(x)` を呼び出して型とそのメモリをリセットします。
