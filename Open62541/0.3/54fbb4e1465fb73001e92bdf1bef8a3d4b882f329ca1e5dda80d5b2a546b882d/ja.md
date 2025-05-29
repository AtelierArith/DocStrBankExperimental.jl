```
Open62541.UA_HistoryEvent_new()::Ptr{Open62541.UA_HistoryEvent}
```

は、Cによってメモリが割り当てられた `Open62541.UA_HistoryEvent` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_HistoryEvent_delete(x::Ptr{Open62541.UA_HistoryEvent})` でクリーンアップする必要があります。
