```
Open62541.UA_EndpointDescription_new()::Ptr{Open62541.UA_EndpointDescription}
```

は、Cによってメモリが割り当てられた `Open62541.UA_EndpointDescription` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_EndpointDescription_delete(x::Ptr{Open62541.UA_EndpointDescription})` でクリーンアップする必要があります。
