```
Float64_copy(src::Ptr{Float64}, dst::Ptr{Float64})::UA_STATUSCODE
Float64_copy(src::Float64, dst::Ptr{Float64})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
