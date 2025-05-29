```
Open62541.UA_ServerState_new()::Ptr{Open62541.UA_ServerState}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ServerState` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ServerState_delete(x::Ptr{Open62541.UA_ServerState})` でクリーンアップする必要があります。
