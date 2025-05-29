```
UInt8_copy(src::Ptr{UInt8}, dst::Ptr{UInt8})::UA_STATUSCODE
UInt8_copy(src::UInt8, dst::Ptr{UInt8})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
