```
Open62541.UA_EventNotificationList_new()::Ptr{Open62541.UA_EventNotificationList}
```

は、Cによってメモリが割り当てられた `Open62541.UA_EventNotificationList` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_EventNotificationList_delete(x::Ptr{Open62541.UA_EventNotificationList})` でクリーンアップする必要があります。
