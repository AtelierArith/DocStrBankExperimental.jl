```
Int64_copy(src::Ptr{Int64}, dst::Ptr{Int64})::UA_STATUSCODE
Int64_copy(src::Int64, dst::Ptr{Int64})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
