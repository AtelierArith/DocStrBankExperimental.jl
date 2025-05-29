```
Open62541.UA_RegisteredServer_deleteMembers(x::Ptr{Open62541.UA_RegisteredServer})
```

(deprecated, use `Open62541.UA_RegisteredServer_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_RegisteredServer_init(x)` to reset the type and its memory.
