```
Int8_copy(src::Ptr{Int8}, dst::Ptr{Int8})::UA_STATUSCODE
Int8_copy(src::Int8, dst::Ptr{Int8})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
