```
Open62541.UA_ExtensionObject_new()::Ptr{Open62541.UA_ExtensionObject}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ExtensionObject` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ExtensionObject_delete(x::Ptr{Open62541.UA_ExtensionObject})` でクリーンアップする必要があります。
