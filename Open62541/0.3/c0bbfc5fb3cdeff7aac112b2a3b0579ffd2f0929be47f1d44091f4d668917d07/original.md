```
Int16_copy(src::Ptr{Int16}, dst::Ptr{Int16})::UA_STATUSCODE
Int16_copy(src::Int16, dst::Ptr{Int16})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
