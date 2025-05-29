```
Float32_deleteMembers(x::Ptr{Float32})
```

(非推奨、代わりに `Float32_clear(x)` を使用してください) は、オブジェクト `x` の動的に割り当てられた内容を削除し、`Float32_init(x)` を呼び出して型とそのメモリをリセットします。
