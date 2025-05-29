```
Open62541.UA_EventFilterResult_deleteMembers(x::Ptr{Open62541.UA_EventFilterResult})
```

(deprecated, use `Open62541.UA_EventFilterResult_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_EventFilterResult_init(x)` to reset the type and its memory.
