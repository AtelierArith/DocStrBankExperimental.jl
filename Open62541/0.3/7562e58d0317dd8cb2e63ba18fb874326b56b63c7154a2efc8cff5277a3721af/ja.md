```
Open62541.UA_RequestHeader_new()::Ptr{Open62541.UA_RequestHeader}
```

は、Cによってメモリが割り当てられた `Open62541.UA_RequestHeader` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_RequestHeader_delete(x::Ptr{Open62541.UA_RequestHeader})` でクリーンアップする必要があります。
