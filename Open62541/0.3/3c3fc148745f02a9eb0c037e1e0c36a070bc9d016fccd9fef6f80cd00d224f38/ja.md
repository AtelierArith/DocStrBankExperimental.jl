```
UA_NODEID_GUID(nsIndex::Integer, identifier::AbstractString)::Ptr{UA_NodeId}
UA_NODEID_GUID(nsIndex::Integer, identifier::Ptr{UA_Guid})::Ptr{UA_NodeId}
```

は、名前空間インデックス `nsIndex` と、グローバルに一意なID（`UA_Guid`）に基づく識別子 `identifier` を使用して `UA_NodeId` オブジェクトを作成します。この識別子は文字列として供給されることも（解析されます）、有効な `Ptr{UA_Guid}` として供給されることもできます。

メモリはCによって割り当てられ、オブジェクトがもはや使用されない場合は `UA_NodeId_delete(x::Ptr{UA_NodeId})` を使用してクリーンアップする必要があります。
