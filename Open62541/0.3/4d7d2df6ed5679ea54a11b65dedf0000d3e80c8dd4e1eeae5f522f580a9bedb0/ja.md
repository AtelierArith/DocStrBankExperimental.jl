```
Open62541.UA_Enumeration_new()::Ptr{Open62541.UA_Enumeration}
```

は、Cによってメモリが割り当てられた `Open62541.UA_Enumeration` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Enumeration_delete(x::Ptr{Open62541.UA_Enumeration})` でクリーンアップする必要があります。
