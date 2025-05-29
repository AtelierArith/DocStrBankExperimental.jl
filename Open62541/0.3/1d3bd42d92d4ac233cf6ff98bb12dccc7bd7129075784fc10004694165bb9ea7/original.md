```
Open62541.UA_SignatureData_deleteMembers(x::Ptr{Open62541.UA_SignatureData})
```

(deprecated, use `Open62541.UA_SignatureData_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_SignatureData_init(x)` to reset the type and its memory.
