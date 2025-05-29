```
Bool_copy(src::Ptr{Bool}, dst::Ptr{Bool})::UA_STATUSCODE
Bool_copy(src::Bool, dst::Ptr{Bool})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
