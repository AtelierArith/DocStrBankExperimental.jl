```
Open62541.UA_SignatureData_new()::Ptr{Open62541.UA_SignatureData}
```

は、Cによってメモリが割り当てられた `Open62541.UA_SignatureData` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_SignatureData_delete(x::Ptr{Open62541.UA_SignatureData})` でクリーンアップする必要があります。
