```
Open62541.UA_ViewAttributes_deleteMembers(x::Ptr{Open62541.UA_ViewAttributes})
```

(deprecated, use `Open62541.UA_ViewAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ViewAttributes_init(x)` to reset the type and its memory.
