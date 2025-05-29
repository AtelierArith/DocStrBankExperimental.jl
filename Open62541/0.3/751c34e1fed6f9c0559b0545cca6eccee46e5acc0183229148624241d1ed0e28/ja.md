```
Open62541.UA_RegisteredServer_new()::Ptr{Open62541.UA_RegisteredServer}
```

は、Cによってメモリが割り当てられた `Open62541.UA_RegisteredServer` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_RegisteredServer_delete(x::Ptr{Open62541.UA_RegisteredServer})` でクリーンアップする必要があります。
