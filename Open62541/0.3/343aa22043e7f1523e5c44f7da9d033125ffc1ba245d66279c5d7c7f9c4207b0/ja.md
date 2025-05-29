```
Bool_copy(src::Ptr{Bool}, dst::Ptr{Bool})::UA_STATUSCODE
Bool_copy(src::Bool, dst::Ptr{Bool})::UA_STATUSCODE
```

ソースオブジェクト `src` の内容をデスティネーションオブジェクト `dst` にコピーします。`UA_STATUSCODE_GOOD` または `UA_STATUSCODE_BADOUTOFMEMORY` を返します。
