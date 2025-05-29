```
Open62541.UA_ReadResponse_copy(src::Ptr{Open62541.UA_ReadResponse}, dst::Ptr{Open62541.UA_ReadResponse})::UA_STATUSCODE
Open62541.UA_ReadResponse_copy(src::Open62541.UA_ReadResponse, dst::Ptr{Open62541.UA_ReadResponse})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
