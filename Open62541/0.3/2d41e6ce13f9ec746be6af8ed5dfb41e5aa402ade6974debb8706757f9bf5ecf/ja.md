```
Open62541.UA_StructureDefinition_new()::Ptr{Open62541.UA_StructureDefinition}
```

は、Cによってメモリが割り当てられた`Open62541.UA_StructureDefinition`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_StructureDefinition_delete(x::Ptr{Open62541.UA_StructureDefinition})`でクリーンアップする必要があります。
