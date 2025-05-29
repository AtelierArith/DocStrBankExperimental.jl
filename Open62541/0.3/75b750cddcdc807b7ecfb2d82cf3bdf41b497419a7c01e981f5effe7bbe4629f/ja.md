```
Open62541.UA_BrowseRequest_new()::Ptr{Open62541.UA_BrowseRequest}
```

は、Cによってメモリが割り当てられた `Open62541.UA_BrowseRequest` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_BrowseRequest_delete(x::Ptr{Open62541.UA_BrowseRequest})` でクリーンアップする必要があります。
