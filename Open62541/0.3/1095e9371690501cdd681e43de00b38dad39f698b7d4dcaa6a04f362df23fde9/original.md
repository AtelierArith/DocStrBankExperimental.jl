```
Open62541.UA_Guid_deleteMembers(x::Ptr{Open62541.UA_Guid})
```

(deprecated, use `Open62541.UA_Guid_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_Guid_init(x)` to reset the type and its memory.
