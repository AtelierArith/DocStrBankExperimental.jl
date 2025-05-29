```
Open62541.UA_RationalNumber_new()::Ptr{Open62541.UA_RationalNumber}
```

は、Cによってメモリが割り当てられた `Open62541.UA_RationalNumber` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_RationalNumber_delete(x::Ptr{Open62541.UA_RationalNumber})` でクリーンアップする必要があります。
