```
Open62541.UA_IdType_new()::Ptr{Open62541.UA_IdType}
```

は、Cによってメモリが割り当てられた `Open62541.UA_IdType` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_IdType_delete(x::Ptr{Open62541.UA_IdType})` でクリーンアップする必要があります。
