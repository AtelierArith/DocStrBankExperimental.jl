```
Open62541.UA_WriteRequest_new()::Ptr{Open62541.UA_WriteRequest}
```

は、Cによってメモリが割り当てられた `Open62541.UA_WriteRequest` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_WriteRequest_delete(x::Ptr{Open62541.UA_WriteRequest})` でクリーンアップする必要があります。
