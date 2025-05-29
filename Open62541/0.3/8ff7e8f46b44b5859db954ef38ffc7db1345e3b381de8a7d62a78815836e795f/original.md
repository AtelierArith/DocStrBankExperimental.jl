```
Open62541.UA_BrowseDescription_deleteMembers(x::Ptr{Open62541.UA_BrowseDescription})
```

(deprecated, use `Open62541.UA_BrowseDescription_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_BrowseDescription_init(x)` to reset the type and its memory.
