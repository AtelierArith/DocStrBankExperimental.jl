```
Open62541.UA_AddNodesResult_deleteMembers(x::Ptr{Open62541.UA_AddNodesResult})
```

(deprecated, use `Open62541.UA_AddNodesResult_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_AddNodesResult_init(x)` to reset the type and its memory.
