```
Float32_copy(src::Ptr{Float32}, dst::Ptr{Float32})::UA_STATUSCODE
Float32_copy(src::Float32, dst::Ptr{Float32})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
