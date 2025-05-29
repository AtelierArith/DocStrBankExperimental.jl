```
UInt64_copy(src::Ptr{UInt64}, dst::Ptr{UInt64})::UA_STATUSCODE
UInt64_copy(src::UInt64, dst::Ptr{UInt64})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
