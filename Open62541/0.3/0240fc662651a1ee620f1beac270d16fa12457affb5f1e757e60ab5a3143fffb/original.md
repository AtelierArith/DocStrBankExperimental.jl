```
Open62541.UA_QueryNextResponse_deleteMembers(x::Ptr{Open62541.UA_QueryNextResponse})
```

(deprecated, use `Open62541.UA_QueryNextResponse_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_QueryNextResponse_init(x)` to reset the type and its memory.
