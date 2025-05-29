```
Open62541.UA_KeyValuePair_deleteMembers(x::Ptr{Open62541.UA_KeyValuePair})
```

(deprecated, use `Open62541.UA_KeyValuePair_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_KeyValuePair_init(x)` to reset the type and its memory.
