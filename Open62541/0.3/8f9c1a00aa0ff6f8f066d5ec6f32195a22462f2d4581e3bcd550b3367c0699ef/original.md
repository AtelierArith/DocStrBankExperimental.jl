```
Open62541.UA_NetworkGroupDataType_deleteMembers(x::Ptr{Open62541.UA_NetworkGroupDataType})
```

(deprecated, use `Open62541.UA_NetworkGroupDataType_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NetworkGroupDataType_init(x)` to reset the type and its memory.
