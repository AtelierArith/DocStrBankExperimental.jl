```
Open62541.UA_Duplex_new()::Ptr{Open62541.UA_Duplex}
```

は、Cによってメモリが割り当てられた`Open62541.UA_Duplex`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Duplex_delete(x::Ptr{Open62541.UA_Duplex})`でクリーンアップする必要があります。
