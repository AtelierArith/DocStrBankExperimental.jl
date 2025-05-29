```
Open62541.UA_QueryFirstRequest_deleteMembers(x::Ptr{Open62541.UA_QueryFirstRequest})
```

(deprecated, use `Open62541.UA_QueryFirstRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_QueryFirstRequest_init(x)` to reset the type and its memory.
