```
Open62541.UA_MethodAttributes_deleteMembers(x::Ptr{Open62541.UA_MethodAttributes})
```

(deprecated, use `Open62541.UA_MethodAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_MethodAttributes_init(x)` to reset the type and its memory.
