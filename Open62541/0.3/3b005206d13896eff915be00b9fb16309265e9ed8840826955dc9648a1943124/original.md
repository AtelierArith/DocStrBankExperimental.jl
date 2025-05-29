```
Open62541.UA_Argument_new()::Ptr{Open62541.UA_Argument}
```

creates and initializes ("zeros") a `Open62541.UA_Argument` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_Argument_delete(x::Ptr{Open62541.UA_Argument})`
