```
Open62541.UA_HistoryEventFieldList_deleteMembers(x::Ptr{Open62541.UA_HistoryEventFieldList})
```

(deprecated, use `Open62541.UA_HistoryEventFieldList_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_HistoryEventFieldList_init(x)` to reset the type and its memory.
