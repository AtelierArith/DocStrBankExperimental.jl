```
Open62541.UA_Range_new()::Ptr{Open62541.UA_Range}
```

は、Cによってメモリが割り当てられた `Open62541.UA_Range` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Range_delete(x::Ptr{Open62541.UA_Range})` でクリーンアップする必要があります。
