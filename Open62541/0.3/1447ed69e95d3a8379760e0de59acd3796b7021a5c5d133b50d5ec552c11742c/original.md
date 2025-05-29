```
Open62541.UA_ReaderGroupDataType_deleteMembers(x::Ptr{Open62541.UA_ReaderGroupDataType})
```

(deprecated, use `Open62541.UA_ReaderGroupDataType_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ReaderGroupDataType_init(x)` to reset the type and its memory.
