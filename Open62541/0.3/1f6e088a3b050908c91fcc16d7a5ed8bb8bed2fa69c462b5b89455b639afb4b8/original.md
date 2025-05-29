```
Open62541.UA_ObjectTypeAttributes_deleteMembers(x::Ptr{Open62541.UA_ObjectTypeAttributes})
```

(deprecated, use `Open62541.UA_ObjectTypeAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ObjectTypeAttributes_init(x)` to reset the type and its memory.
