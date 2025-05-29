```
Open62541.UA_Guid_new()::Ptr{Open62541.UA_Guid}
```

creates and initializes ("zeros") a `Open62541.UA_Guid` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_Guid_delete(x::Ptr{Open62541.UA_Guid})`
