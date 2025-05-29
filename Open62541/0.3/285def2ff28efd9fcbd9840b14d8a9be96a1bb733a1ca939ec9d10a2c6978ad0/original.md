```
Open62541.UA_ReferenceNode_deleteMembers(x::Ptr{Open62541.UA_ReferenceNode})
```

(deprecated, use `Open62541.UA_ReferenceNode_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReferenceNode_init(x)` to reset the type and its memory.
