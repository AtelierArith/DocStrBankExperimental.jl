```
Open62541.UA_BrowsePath_new()::Ptr{Open62541.UA_BrowsePath}
```

は、Cによってメモリが割り当てられた`Open62541.UA_BrowsePath`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_BrowsePath_delete(x::Ptr{Open62541.UA_BrowsePath})`でクリーンアップする必要があります。
