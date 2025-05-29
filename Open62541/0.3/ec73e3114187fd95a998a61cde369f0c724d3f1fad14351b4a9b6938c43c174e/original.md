```
Open62541.UA_OptionSet_deleteMembers(x::Ptr{Open62541.UA_OptionSet})
```

(deprecated, use `Open62541.UA_OptionSet_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_OptionSet_init(x)` to reset the type and its memory.
