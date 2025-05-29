```
Open62541.UA_ReadEventDetails_deleteMembers(x::Ptr{Open62541.UA_ReadEventDetails})
```

(deprecated, use `Open62541.UA_ReadEventDetails_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReadEventDetails_init(x)` to reset the type and its memory.
