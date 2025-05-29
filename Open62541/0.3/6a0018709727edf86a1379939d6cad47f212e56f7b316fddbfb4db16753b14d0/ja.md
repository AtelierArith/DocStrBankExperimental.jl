```
UA_NODEID_BYTESTRING_ALLOC(nsIndex::Integer, identifier::AbstractString)::Ptr{UA_NodeId}
UA_NODEID_BYTESTRING_ALLOC(nsIndex::Integer, identifier::Ptr{UA_ByteString})::Ptr{UA_NodeId}
```

は、名前空間インデックス `nsIndex` とバイト文字列識別子 `identifier`（文字列または UA*ByteString である可能性があります）を持つ `UA*NodeId` オブジェクトを作成します。

メモリは C によって割り当てられ、オブジェクトがもはや使用されない場合は `UA_NodeId_delete(x::Ptr{UA_NodeId})` を使用してクリーンアップする必要があります。
