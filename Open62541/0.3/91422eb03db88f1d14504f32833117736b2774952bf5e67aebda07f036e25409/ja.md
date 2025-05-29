```
Open62541.UA_EnumField_new()::Ptr{Open62541.UA_EnumField}
```

は、Cによってメモリが割り当てられた `Open62541.UA_EnumField` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_EnumField_delete(x::Ptr{Open62541.UA_EnumField})` でクリーンアップする必要があります。
