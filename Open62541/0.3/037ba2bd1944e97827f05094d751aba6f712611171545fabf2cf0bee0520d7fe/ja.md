```
Open62541.UA_OptionSet_new()::Ptr{Open62541.UA_OptionSet}
```

は、Cによってメモリが割り当てられた`Open62541.UA_OptionSet`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_OptionSet_delete(x::Ptr{Open62541.UA_OptionSet})`でクリーンアップする必要があります。
