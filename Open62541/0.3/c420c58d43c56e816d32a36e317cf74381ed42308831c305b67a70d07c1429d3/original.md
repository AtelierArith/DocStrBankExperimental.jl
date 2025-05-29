```
Open62541.UA_WriteRequest_deleteMembers(x::Ptr{Open62541.UA_WriteRequest})
```

(deprecated, use `Open62541.UA_WriteRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_WriteRequest_init(x)` to reset the type and its memory.
