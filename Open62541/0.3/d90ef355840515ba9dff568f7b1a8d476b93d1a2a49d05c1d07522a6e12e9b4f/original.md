```
Open62541.UA_NodeAttributes_deleteMembers(x::Ptr{Open62541.UA_NodeAttributes})
```

(deprecated, use `Open62541.UA_NodeAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NodeAttributes_init(x)` to reset the type and its memory.
