```
Open62541.UA_PubSubState_new()::Ptr{Open62541.UA_PubSubState}
```

は、Cによってメモリが割り当てられた `Open62541.UA_PubSubState` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_PubSubState_delete(x::Ptr{Open62541.UA_PubSubState})` でクリーンアップする必要があります。
