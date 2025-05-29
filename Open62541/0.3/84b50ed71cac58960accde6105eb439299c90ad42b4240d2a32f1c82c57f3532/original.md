```
Open62541.UA_RegisterNodesRequest_deleteMembers(x::Ptr{Open62541.UA_RegisterNodesRequest})
```

(deprecated, use `Open62541.UA_RegisterNodesRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_RegisterNodesRequest_init(x)` to reset the type and its memory.
