```
Open62541.UA_VariableAttributes_new()::Ptr{Open62541.UA_VariableAttributes}
```

は、Cによってメモリが割り当てられた `Open62541.UA_VariableAttributes` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_VariableAttributes_delete(x::Ptr{Open62541.UA_VariableAttributes})` でクリーンアップする必要があります。
