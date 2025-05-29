```
Open62541.UA_HistoryModifiedData_deleteMembers(x::Ptr{Open62541.UA_HistoryModifiedData})
```

(deprecated, use `Open62541.UA_HistoryModifiedData_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_HistoryModifiedData_init(x)` to reset the type and its memory.
