```
Open62541.UA_Guid_new()::Ptr{Open62541.UA_Guid}
```

は、Cによってメモリが割り当てられた`Open62541.UA_Guid`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Guid_delete(x::Ptr{Open62541.UA_Guid})`でクリーンアップする必要があります。
