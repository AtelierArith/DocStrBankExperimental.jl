```
Open62541.UA_BuildInfo_new()::Ptr{Open62541.UA_BuildInfo}
```

creates and initializes ("zeros") a `Open62541.UA_BuildInfo` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_BuildInfo_delete(x::Ptr{Open62541.UA_BuildInfo})`
