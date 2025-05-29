```
Open62541.UA_EventFilter_deleteMembers(x::Ptr{Open62541.UA_EventFilter})
```

(deprecated, use `Open62541.UA_EventFilter_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_EventFilter_init(x)` to reset the type and its memory.
