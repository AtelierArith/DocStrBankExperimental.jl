```
Open62541.UA_FilterOperator_deleteMembers(x::Ptr{Open62541.UA_FilterOperator})
```

(deprecated, use `Open62541.UA_FilterOperator_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_FilterOperator_init(x)` to reset the type and its memory.
