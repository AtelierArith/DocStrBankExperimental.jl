```
Float64_copy(src::Ptr{Float64}, dst::Ptr{Float64})::UA_STATUSCODE
Float64_copy(src::Float64, dst::Ptr{Float64})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容を宛先オブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
