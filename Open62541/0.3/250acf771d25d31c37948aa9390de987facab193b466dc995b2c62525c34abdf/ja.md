```
Open62541.UA_CallRequest_new()::Ptr{Open62541.UA_CallRequest}
```

は、Cによってメモリが割り当てられた `Open62541.UA_CallRequest` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_CallRequest_delete(x::Ptr{Open62541.UA_CallRequest})` でクリーンアップする必要があります。
