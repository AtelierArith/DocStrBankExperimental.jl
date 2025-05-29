```
Open62541.UA_ModificationInfo_deleteMembers(x::Ptr{Open62541.UA_ModificationInfo})
```

(deprecated, use `Open62541.UA_ModificationInfo_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ModificationInfo_init(x)` to reset the type and its memory.
