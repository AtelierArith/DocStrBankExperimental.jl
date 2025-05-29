```
Int8_copy(src::Ptr{Int8}, dst::Ptr{Int8})::UA_STATUSCODE
Int8_copy(src::Int8, dst::Ptr{Int8})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
