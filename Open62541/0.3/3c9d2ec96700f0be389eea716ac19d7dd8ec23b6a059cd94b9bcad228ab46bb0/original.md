```
Open62541.UA_ViewDescription_deleteMembers(x::Ptr{Open62541.UA_ViewDescription})
```

(deprecated, use `Open62541.UA_ViewDescription_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ViewDescription_init(x)` to reset the type and its memory.
