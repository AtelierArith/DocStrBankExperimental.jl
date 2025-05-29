```
Open62541.UA_NodeAttributes_new()::Ptr{Open62541.UA_NodeAttributes}
```

は、Cによってメモリが割り当てられた `Open62541.UA_NodeAttributes` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_NodeAttributes_delete(x::Ptr{Open62541.UA_NodeAttributes})` でクリーンアップする必要があります。
