```
Open62541.UA_IdType_copy(src::Ptr{Open62541.UA_IdType}, dst::Ptr{Open62541.UA_IdType})::UA_STATUSCODE
Open62541.UA_IdType_copy(src::Open62541.UA_IdType, dst::Ptr{Open62541.UA_IdType})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
