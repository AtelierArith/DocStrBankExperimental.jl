```
Open62541.UA_RegisterServerRequest_deleteMembers(x::Ptr{Open62541.UA_RegisterServerRequest})
```

(deprecated, use `Open62541.UA_RegisterServerRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_RegisterServerRequest_init(x)` to reset the type and its memory.
