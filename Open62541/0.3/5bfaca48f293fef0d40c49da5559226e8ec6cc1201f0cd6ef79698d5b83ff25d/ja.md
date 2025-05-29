```
Open62541.UA_KeyValuePair_new()::Ptr{Open62541.UA_KeyValuePair}
```

は、Cによってメモリが割り当てられた `Open62541.UA_KeyValuePair` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_KeyValuePair_delete(x::Ptr{Open62541.UA_KeyValuePair})` でクリーンアップする必要があります。
