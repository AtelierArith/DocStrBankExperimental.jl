```
Open62541.UA_FieldMetaData_deleteMembers(x::Ptr{Open62541.UA_FieldMetaData})
```

(deprecated, use `Open62541.UA_FieldMetaData_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_FieldMetaData_init(x)` to reset the type and its memory.
