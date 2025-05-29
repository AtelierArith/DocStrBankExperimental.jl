```
Open62541.UA_DataTypeAttributes_deleteMembers(x::Ptr{Open62541.UA_DataTypeAttributes})
```

(deprecated, use `Open62541.UA_DataTypeAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_DataTypeAttributes_init(x)` to reset the type and its memory.
