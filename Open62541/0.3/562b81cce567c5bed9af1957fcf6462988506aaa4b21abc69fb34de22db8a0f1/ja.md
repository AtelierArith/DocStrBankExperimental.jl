```
UA_NODEID_NUMERIC(nsIndex::Integer, identifier::Integer)::Ptr{UA_NodeId}
```

は、名前空間インデックス `nsIndex` と数値識別子 `identifier` を持つ `UA_NodeId` オブジェクトを作成します。メモリはCによって割り当てられ、オブジェクトがもはや使用されない場合は `UA_NodeId_delete(x::Ptr{UA_NodeId})` を使用してクリーンアップする必要があります。
