```
Open62541.UA_OpenFileMode_copy(src::Ptr{Open62541.UA_OpenFileMode}, dst::Ptr{Open62541.UA_OpenFileMode})::UA_STATUSCODE
Open62541.UA_OpenFileMode_copy(src::Open62541.UA_OpenFileMode, dst::Ptr{Open62541.UA_OpenFileMode})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
