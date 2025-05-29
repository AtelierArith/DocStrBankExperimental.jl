```
Open62541.UA_CallResponse_copy(src::Ptr{Open62541.UA_CallResponse}, dst::Ptr{Open62541.UA_CallResponse})::UA_STATUSCODE
Open62541.UA_CallResponse_copy(src::Open62541.UA_CallResponse, dst::Ptr{Open62541.UA_CallResponse})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
