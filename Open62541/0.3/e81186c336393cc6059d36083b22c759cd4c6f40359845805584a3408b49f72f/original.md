```
Open62541.UA_NodeReference_deleteMembers(x::Ptr{Open62541.UA_NodeReference})
```

(deprecated, use `Open62541.UA_NodeReference_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NodeReference_init(x)` to reset the type and its memory.
