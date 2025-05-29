```
Bool_deleteMembers(x::Ptr{Bool})
```

（非推奨、代わりに `Bool_clear(x)` を使用してください）オブジェクト `x` の動的に割り当てられた内容を削除し、型とそのメモリをリセットするために `Bool_init(x)` を呼び出します。
