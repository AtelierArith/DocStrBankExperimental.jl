```
Open62541.UA_String_new()::Ptr{Open62541.UA_String}
```

は、Cによってメモリが割り当てられた `Open62541.UA_String` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_String_delete(x::Ptr{Open62541.UA_String})` でクリーンアップする必要があります。
