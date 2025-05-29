```
Open62541.UA_NotificationMessage_new()::Ptr{Open62541.UA_NotificationMessage}
```

は、Cによってメモリが割り当てられた`Open62541.UA_NotificationMessage`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_NotificationMessage_delete(x::Ptr{Open62541.UA_NotificationMessage})`でクリーンアップする必要があります。
