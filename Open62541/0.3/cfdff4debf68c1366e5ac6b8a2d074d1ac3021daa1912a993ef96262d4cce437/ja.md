```
Float32_copy(src::Ptr{Float32}, dst::Ptr{Float32})::UA_STATUSCODE
Float32_copy(src::Float32, dst::Ptr{Float32})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
