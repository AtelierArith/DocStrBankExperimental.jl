```
Open62541.UA_StructureField_new()::Ptr{Open62541.UA_StructureField}
```

は、Cによってメモリが割り当てられた `Open62541.UA_StructureField` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_StructureField_delete(x::Ptr{Open62541.UA_StructureField})` でクリーンアップする必要があります。
