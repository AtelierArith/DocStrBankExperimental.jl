```
Int32_copy(src::Ptr{Int32}, dst::Ptr{Int32})::UA_STATUSCODE
Int32_copy(src::Int32, dst::Ptr{Int32})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
