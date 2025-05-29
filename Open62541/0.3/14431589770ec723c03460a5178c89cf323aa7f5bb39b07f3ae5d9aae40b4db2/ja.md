```
Open62541.UA_GenericAttributeValue_new()::Ptr{Open62541.UA_GenericAttributeValue}
```

は、Cによってメモリが割り当てられた `Open62541.UA_GenericAttributeValue` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_GenericAttributeValue_delete(x::Ptr{Open62541.UA_GenericAttributeValue})` でクリーンアップする必要があります。
