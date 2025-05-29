```
Open62541.UA_QualifiedName_new()::Ptr{Open62541.UA_QualifiedName}
```

は、Cによってメモリが割り当てられた `Open62541.UA_QualifiedName` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_QualifiedName_delete(x::Ptr{Open62541.UA_QualifiedName})` でクリーンアップする必要があります。
