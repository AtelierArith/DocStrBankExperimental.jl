```
Open62541.UA_NodeClass_new()::Ptr{Open62541.UA_NodeClass}
```

は、Cによってメモリが割り当てられた `Open62541.UA_NodeClass` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_NodeClass_delete(x::Ptr{Open62541.UA_NodeClass})` でクリーンアップする必要があります。
