```
Open62541.UA_HistoryEvent_deleteMembers(x::Ptr{Open62541.UA_HistoryEvent})
```

(deprecated, use `Open62541.UA_HistoryEvent_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_HistoryEvent_init(x)` to reset the type and its memory.
