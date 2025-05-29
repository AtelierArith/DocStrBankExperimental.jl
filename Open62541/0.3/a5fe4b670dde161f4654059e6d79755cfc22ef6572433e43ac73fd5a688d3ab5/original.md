```
Open62541.UA_StatusResult_copy(src::Ptr{Open62541.UA_StatusResult}, dst::Ptr{Open62541.UA_StatusResult})::UA_STATUSCODE
Open62541.UA_StatusResult_copy(src::Open62541.UA_StatusResult, dst::Ptr{Open62541.UA_StatusResult})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
