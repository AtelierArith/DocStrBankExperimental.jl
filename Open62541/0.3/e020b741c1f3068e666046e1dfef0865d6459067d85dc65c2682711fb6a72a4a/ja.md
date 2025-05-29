```
Float64_deleteMembers(x::Ptr{Float64})
```

（非推奨、代わりに `Float64_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、`Float64_init(x)` を呼び出して型とそのメモリをリセットします。
