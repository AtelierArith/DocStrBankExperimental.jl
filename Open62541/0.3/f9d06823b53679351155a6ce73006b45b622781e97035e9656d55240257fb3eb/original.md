```
Open62541.UA_IdType_deleteMembers(x::Ptr{Open62541.UA_IdType})
```

(deprecated, use `Open62541.UA_IdType_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_IdType_init(x)` to reset the type and its memory.
