```
UInt16_copy(src::Ptr{UInt16}, dst::Ptr{UInt16})::UA_STATUSCODE
UInt16_copy(src::UInt16, dst::Ptr{UInt16})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
