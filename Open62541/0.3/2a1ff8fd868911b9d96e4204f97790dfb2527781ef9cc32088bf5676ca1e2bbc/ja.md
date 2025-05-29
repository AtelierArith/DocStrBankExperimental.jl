```
Open62541.UA_ReferenceNode_new()::Ptr{Open62541.UA_ReferenceNode}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ReferenceNode` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ReferenceNode_delete(x::Ptr{Open62541.UA_ReferenceNode})` でクリーンアップする必要があります。
