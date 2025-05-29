```
Open62541.UA_BrowsePathTarget_deleteMembers(x::Ptr{Open62541.UA_BrowsePathTarget})
```

(deprecated, use `Open62541.UA_BrowsePathTarget_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_BrowsePathTarget_init(x)` to reset the type and its memory.
