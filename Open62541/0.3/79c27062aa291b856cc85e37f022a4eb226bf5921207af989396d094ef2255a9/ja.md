```
Open62541.UA_Range_deleteMembers(x::Ptr{Open62541.UA_Range})
```

(非推奨、代わりに `Open62541.UA_Range_clear(x)` を使用してください) オブジェクト `x` の動的に割り当てられた内容を削除し、`Open62541.UA_Range_init(x)` を呼び出して型とそのメモリをリセットします。
