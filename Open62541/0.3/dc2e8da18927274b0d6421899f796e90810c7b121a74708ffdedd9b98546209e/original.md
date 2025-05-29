```
Open62541.UA_WriteValue_deleteMembers(x::Ptr{Open62541.UA_WriteValue})
```

(deprecated, use `Open62541.UA_WriteValue_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_WriteValue_init(x)` to reset the type and its memory.
