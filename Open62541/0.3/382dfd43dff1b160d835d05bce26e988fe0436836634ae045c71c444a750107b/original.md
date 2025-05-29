```
Int32_copy(src::Ptr{Int32}, dst::Ptr{Int32})::UA_STATUSCODE
Int32_copy(src::Int32, dst::Ptr{Int32})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
