```
UInt32_copy(src::Ptr{UInt32}, dst::Ptr{UInt32})::UA_STATUSCODE
UInt32_copy(src::UInt32, dst::Ptr{UInt32})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
