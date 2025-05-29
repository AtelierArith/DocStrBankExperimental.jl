```
Open62541.UA_ReferenceTypeAttributes_deleteMembers(x::Ptr{Open62541.UA_ReferenceTypeAttributes})
```

(deprecated, use `Open62541.UA_ReferenceTypeAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReferenceTypeAttributes_init(x)` to reset the type and its memory.
