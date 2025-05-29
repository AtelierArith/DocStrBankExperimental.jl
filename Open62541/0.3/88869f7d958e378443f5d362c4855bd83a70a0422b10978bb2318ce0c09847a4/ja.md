```
Open62541.UA_NodeReference_new()::Ptr{Open62541.UA_NodeReference}
```

は、Cによってメモリが割り当てられた `Open62541.UA_NodeReference` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_NodeReference_delete(x::Ptr{Open62541.UA_NodeReference})` でクリーンアップする必要があります。
