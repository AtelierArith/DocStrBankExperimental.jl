```
UInt32_copy(src::Ptr{UInt32}, dst::Ptr{UInt32})::UA_STATUSCODE
UInt32_copy(src::UInt32, dst::Ptr{UInt32})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
