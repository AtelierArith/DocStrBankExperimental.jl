```
Open62541.UA_ResponseHeader_new()::Ptr{Open62541.UA_ResponseHeader}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ResponseHeader` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ResponseHeader_delete(x::Ptr{Open62541.UA_ResponseHeader})` でクリーンアップする必要があります。
