```
Open62541.UA_Argument_new()::Ptr{Open62541.UA_Argument}
```

は、Cによってメモリが割り当てられた `Open62541.UA_Argument` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Argument_delete(x::Ptr{Open62541.UA_Argument})` でクリーンアップする必要があります。
