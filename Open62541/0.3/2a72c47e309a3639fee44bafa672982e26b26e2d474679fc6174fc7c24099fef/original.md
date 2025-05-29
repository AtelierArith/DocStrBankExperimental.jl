```
Open62541.UA_Annotation_new()::Ptr{Open62541.UA_Annotation}
```

creates and initializes ("zeros") a `Open62541.UA_Annotation` object whose memory is allocated by C. After use, it needs to be  cleaned up with `Open62541.UA_Annotation_delete(x::Ptr{Open62541.UA_Annotation})`
