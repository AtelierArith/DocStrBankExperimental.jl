```
Int64_deleteMembers(x::Ptr{Int64})
```

(非推奨、代わりに `Int64_clear(x)` を使用してください) は、オブジェクト `x` の動的に割り当てられた内容を削除し、`Int64_init(x)` を呼び出して型とそのメモリをリセットします。
