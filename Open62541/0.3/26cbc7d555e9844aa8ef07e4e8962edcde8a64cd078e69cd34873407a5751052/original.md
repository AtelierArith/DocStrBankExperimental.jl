```
Open62541.UA_WriteResponse_deleteMembers(x::Ptr{Open62541.UA_WriteResponse})
```

(deprecated, use `Open62541.UA_WriteResponse_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_WriteResponse_init(x)` to reset the type and its memory.
