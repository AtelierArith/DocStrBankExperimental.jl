```
Open62541.UA_DeleteNodesItem_deleteMembers(x::Ptr{Open62541.UA_DeleteNodesItem})
```

(deprecated, use `Open62541.UA_DeleteNodesItem_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_DeleteNodesItem_init(x)` to reset the type and its memory.
