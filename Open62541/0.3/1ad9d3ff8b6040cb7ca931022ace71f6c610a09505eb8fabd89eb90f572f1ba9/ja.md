```
Open62541.UA_BrowsePath_deleteMembers(x::Ptr{Open62541.UA_BrowsePath})
```

(非推奨、代わりに `Open62541.UA_BrowsePath_clear(x)` を使用してください) は、オブジェクト `x` の動的に割り当てられた内容を削除し、`Open62541.UA_BrowsePath_init(x)` を呼び出して型とそのメモリをリセットします。
