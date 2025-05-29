```
Open62541.UA_NodeId_deleteMembers(x::Ptr{Open62541.UA_NodeId})
```

(deprecated, use `Open62541.UA_NodeId_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NodeId_init(x)` to reset the type and its memory.
