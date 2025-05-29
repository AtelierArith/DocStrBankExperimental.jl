```
Open62541.UA_ServerState_deleteMembers(x::Ptr{Open62541.UA_ServerState})
```

(deprecated, use `Open62541.UA_ServerState_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ServerState_init(x)` to reset the type and its memory.
