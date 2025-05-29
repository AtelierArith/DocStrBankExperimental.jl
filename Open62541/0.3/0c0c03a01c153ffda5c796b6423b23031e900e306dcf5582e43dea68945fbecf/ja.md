```
Open62541.UA_Variant_new()::Ptr{Open62541.UA_Variant}
```

は、Cによってメモリが割り当てられた`Open62541.UA_Variant`オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_Variant_delete(x::Ptr{Open62541.UA_Variant})`でクリーンアップする必要があります。
