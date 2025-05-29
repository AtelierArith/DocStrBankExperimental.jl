```
Open62541.UA_QueryDataDescription_deleteMembers(x::Ptr{Open62541.UA_QueryDataDescription})
```

(deprecated, use `Open62541.UA_QueryDataDescription_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_QueryDataDescription_init(x)` to reset the type and its memory.
