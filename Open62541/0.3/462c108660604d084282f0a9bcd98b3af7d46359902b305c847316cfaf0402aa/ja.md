```
Open62541.UA_AttributeOperand_new()::Ptr{Open62541.UA_AttributeOperand}
```

は、Cによってメモリが割り当てられた `Open62541.UA_AttributeOperand` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_AttributeOperand_delete(x::Ptr{Open62541.UA_AttributeOperand})` でクリーンアップする必要があります。
