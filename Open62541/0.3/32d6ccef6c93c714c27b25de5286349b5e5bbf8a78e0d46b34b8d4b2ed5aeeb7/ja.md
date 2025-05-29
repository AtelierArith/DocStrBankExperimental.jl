```
Open62541.UA_ElementOperand_new()::Ptr{Open62541.UA_ElementOperand}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ElementOperand` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ElementOperand_delete(x::Ptr{Open62541.UA_ElementOperand})` でクリーンアップする必要があります。
