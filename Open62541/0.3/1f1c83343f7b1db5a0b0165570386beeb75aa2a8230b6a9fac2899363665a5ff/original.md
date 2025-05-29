```
Open62541.UA_CallRequest_deleteMembers(x::Ptr{Open62541.UA_CallRequest})
```

(deprecated, use `Open62541.UA_CallRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_CallRequest_init(x)` to reset the type and its memory.
