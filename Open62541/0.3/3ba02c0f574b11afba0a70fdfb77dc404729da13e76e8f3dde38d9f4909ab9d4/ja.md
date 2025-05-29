```
UInt16_copy(src::Ptr{UInt16}, dst::Ptr{UInt16})::UA_STATUSCODE
UInt16_copy(src::UInt16, dst::Ptr{UInt16})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
