```
Open62541.UA_Variant_new()::Ptr{Open62541.UA_Variant}
```

creates and initializes ("zeros") a `Open62541.UA_Variant` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_Variant_delete(x::Ptr{Open62541.UA_Variant})`
