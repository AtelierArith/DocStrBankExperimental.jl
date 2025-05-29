```
Open62541.UA_QueryDataSet_new()::Ptr{Open62541.UA_QueryDataSet}
```

は、Cによってメモリが割り当てられた`Open62541.UA_QueryDataSet`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_QueryDataSet_delete(x::Ptr{Open62541.UA_QueryDataSet})`でクリーンアップする必要があります。
