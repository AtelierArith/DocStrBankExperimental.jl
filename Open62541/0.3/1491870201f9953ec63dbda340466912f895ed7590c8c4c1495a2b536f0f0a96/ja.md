```
Open62541.UA_BuildInfo_new()::Ptr{Open62541.UA_BuildInfo}
```

は、Cによってメモリが割り当てられた`Open62541.UA_BuildInfo`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_BuildInfo_delete(x::Ptr{Open62541.UA_BuildInfo})`でクリーンアップする必要があります。
