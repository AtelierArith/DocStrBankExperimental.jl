```
Open62541.UA_Duplex_deleteMembers(x::Ptr{Open62541.UA_Duplex})
```

(deprecated, use `Open62541.UA_Duplex_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_Duplex_init(x)` to reset the type and its memory.
