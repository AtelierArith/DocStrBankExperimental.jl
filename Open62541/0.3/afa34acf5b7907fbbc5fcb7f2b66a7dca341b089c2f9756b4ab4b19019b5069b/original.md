```
Open62541.UA_DataValue_deleteMembers(x::Ptr{Open62541.UA_DataValue})
```

(deprecated, use `Open62541.UA_DataValue_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_DataValue_init(x)` to reset the type and its memory.
