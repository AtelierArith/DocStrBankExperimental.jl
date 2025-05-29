```
Open62541.UA_BrowseRequest_deleteMembers(x::Ptr{Open62541.UA_BrowseRequest})
```

(deprecated, use `Open62541.UA_BrowseRequest_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_BrowseRequest_init(x)` to reset the type and its memory.
