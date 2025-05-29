```
UInt64_copy(src::Ptr{UInt64}, dst::Ptr{UInt64})::UA_STATUSCODE
UInt64_copy(src::UInt64, dst::Ptr{UInt64})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
