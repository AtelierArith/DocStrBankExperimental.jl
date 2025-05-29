```
Open62541.UA_NodeClass_deleteMembers(x::Ptr{Open62541.UA_NodeClass})
```

(deprecated, use `Open62541.UA_NodeClass_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NodeClass_init(x)` to reset the type and its memory.
