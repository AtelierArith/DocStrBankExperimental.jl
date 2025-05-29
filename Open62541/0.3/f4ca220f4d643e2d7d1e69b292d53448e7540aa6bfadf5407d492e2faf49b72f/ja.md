```
Open62541.UA_StructureType_new()::Ptr{Open62541.UA_StructureType}
```

は、Cによってメモリが割り当てられた `Open62541.UA_StructureType` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_StructureType_delete(x::Ptr{Open62541.UA_StructureType})` でクリーンアップする必要があります。
