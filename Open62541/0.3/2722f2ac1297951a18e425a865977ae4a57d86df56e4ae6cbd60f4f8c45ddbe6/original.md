```
Open62541.UA_ReadRequest_deleteMembers(x::Ptr{Open62541.UA_ReadRequest})
```

(deprecated, use `Open62541.UA_ReadRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReadRequest_init(x)` to reset the type and its memory.
