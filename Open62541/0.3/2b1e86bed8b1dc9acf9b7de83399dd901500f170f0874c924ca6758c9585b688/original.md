```
UInt8_copy(src::Ptr{UInt8}, dst::Ptr{UInt8})::UA_STATUSCODE
UInt8_copy(src::UInt8, dst::Ptr{UInt8})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
