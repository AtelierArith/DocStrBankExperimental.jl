```
Open62541.UA_GenericAttributes_new()::Ptr{Open62541.UA_GenericAttributes}
```

は、Cによってメモリが割り当てられた `Open62541.UA_GenericAttributes` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_GenericAttributes_delete(x::Ptr{Open62541.UA_GenericAttributes})` でクリーンアップする必要があります。
