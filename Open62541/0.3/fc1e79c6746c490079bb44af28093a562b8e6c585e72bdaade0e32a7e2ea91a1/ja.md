```
Open62541.UA_StatusResult_new()::Ptr{Open62541.UA_StatusResult}
```

は、Cによってメモリが割り当てられた `Open62541.UA_StatusResult` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_StatusResult_delete(x::Ptr{Open62541.UA_StatusResult})` でクリーンアップする必要があります。
