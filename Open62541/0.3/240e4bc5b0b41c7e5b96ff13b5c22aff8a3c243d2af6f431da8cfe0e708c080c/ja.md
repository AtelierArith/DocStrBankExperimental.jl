```
Open62541.UA_ReadRequest_new()::Ptr{Open62541.UA_ReadRequest}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ReadRequest` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ReadRequest_delete(x::Ptr{Open62541.UA_ReadRequest})` でクリーンアップする必要があります。
