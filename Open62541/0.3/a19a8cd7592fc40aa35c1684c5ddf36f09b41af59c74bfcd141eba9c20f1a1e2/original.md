```
Open62541.UA_DataValue_new()::Ptr{Open62541.UA_DataValue}
```

creates and initializes ("zeros") a `Open62541.UA_DataValue` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_DataValue_delete(x::Ptr{Open62541.UA_DataValue})`
