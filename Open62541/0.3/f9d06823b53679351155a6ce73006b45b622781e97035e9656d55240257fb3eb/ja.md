```
Open62541.UA_IdType_deleteMembers(x::Ptr{Open62541.UA_IdType})
```

(非推奨、代わりに `Open62541.UA_IdType_clear(x)` を使用してください) は、オブジェクト `x` の動的に割り当てられた内容を削除し、`Open62541.UA_IdType_init(x)` を呼び出して型とそのメモリをリセットします。
