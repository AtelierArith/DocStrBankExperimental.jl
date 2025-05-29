```
Int64_copy(src::Ptr{Int64}, dst::Ptr{Int64})::UA_STATUSCODE
Int64_copy(src::Int64, dst::Ptr{Int64})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
