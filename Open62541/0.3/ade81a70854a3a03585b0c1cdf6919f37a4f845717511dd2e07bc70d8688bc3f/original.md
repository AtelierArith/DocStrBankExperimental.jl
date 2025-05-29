```
Open62541.UA_AddReferencesItem_deleteMembers(x::Ptr{Open62541.UA_AddReferencesItem})
```

(deprecated, use `Open62541.UA_AddReferencesItem_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_AddReferencesItem_init(x)` to reset the type and its memory.
