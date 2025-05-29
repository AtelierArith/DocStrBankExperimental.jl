```
Open62541.UA_AddNodesItem_deleteMembers(x::Ptr{Open62541.UA_AddNodesItem})
```

(deprecated, use `Open62541.UA_AddNodesItem_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_AddNodesItem_init(x)` to reset the type and its memory.
