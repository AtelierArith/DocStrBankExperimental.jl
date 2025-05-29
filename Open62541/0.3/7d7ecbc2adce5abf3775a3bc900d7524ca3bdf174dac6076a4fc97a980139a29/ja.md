```
Open62541.UA_ObjectAttributes_new()::Ptr{Open62541.UA_ObjectAttributes}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ObjectAttributes` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ObjectAttributes_delete(x::Ptr{Open62541.UA_ObjectAttributes})` でクリーンアップする必要があります。
