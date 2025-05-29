```
Open62541.UA_BrowseResult_new()::Ptr{Open62541.UA_BrowseResult}
```

は、Cによってメモリが割り当てられた `Open62541.UA_BrowseResult` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_BrowseResult_delete(x::Ptr{Open62541.UA_BrowseResult})` でクリーンアップする必要があります。
