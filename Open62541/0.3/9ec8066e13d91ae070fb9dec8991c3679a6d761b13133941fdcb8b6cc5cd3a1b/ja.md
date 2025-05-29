```
Open62541.UA_NodeId_new()::Ptr{Open62541.UA_NodeId}
```

は、Cによってメモリが割り当てられた `Open62541.UA_NodeId` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_NodeId_delete(x::Ptr{Open62541.UA_NodeId})` でクリーンアップする必要があります。
