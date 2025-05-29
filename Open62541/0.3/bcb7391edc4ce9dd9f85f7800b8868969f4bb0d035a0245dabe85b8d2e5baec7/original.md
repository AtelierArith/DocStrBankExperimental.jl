```
Open62541.UA_ReadResponse_deleteMembers(x::Ptr{Open62541.UA_ReadResponse})
```

(deprecated, use `Open62541.UA_ReadResponse_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReadResponse_init(x)` to reset the type and its memory.
