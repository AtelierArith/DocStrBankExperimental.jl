```
Open62541.UA_StructureField_deleteMembers(x::Ptr{Open62541.UA_StructureField})
```

(非推奨、代わりに `Open62541.UA_StructureField_clear(x)` を使用してください) オブジェクト `x` の動的に割り当てられた内容を削除し、`Open62541.UA_StructureField_init(x)` を呼び出して型とそのメモリをリセットします。
