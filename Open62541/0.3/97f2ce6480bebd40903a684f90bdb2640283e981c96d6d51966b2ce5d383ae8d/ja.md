```
Open62541.UA_ViewAttributes_new()::Ptr{Open62541.UA_ViewAttributes}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ViewAttributes` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ViewAttributes_delete(x::Ptr{Open62541.UA_ViewAttributes})` でクリーンアップする必要があります。
