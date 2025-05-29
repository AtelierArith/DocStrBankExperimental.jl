```
Int16_copy(src::Ptr{Int16}, dst::Ptr{Int16})::UA_STATUSCODE
Int16_copy(src::Int16, dst::Ptr{Int16})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
