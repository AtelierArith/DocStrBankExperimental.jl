```
Open62541.UA_ThreeDVector_new()::Ptr{Open62541.UA_ThreeDVector}
```

は、Cによってメモリが割り当てられた `Open62541.UA_ThreeDVector` オブジェクトを作成し、初期化（"ゼロ"）します。使用後は、`Open62541.UA_ThreeDVector_delete(x::Ptr{Open62541.UA_ThreeDVector})` でクリーンアップする必要があります。
