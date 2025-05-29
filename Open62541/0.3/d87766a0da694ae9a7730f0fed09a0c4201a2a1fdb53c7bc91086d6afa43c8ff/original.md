```
Open62541.UA_BuildInfo_deleteMembers(x::Ptr{Open62541.UA_BuildInfo})
```

(deprecated, use `Open62541.UA_BuildInfo_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_BuildInfo_init(x)` to reset the type and its memory.
