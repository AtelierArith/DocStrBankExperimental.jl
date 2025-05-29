```
Open62541.UA_Argument_deleteMembers(x::Ptr{Open62541.UA_Argument})
```

(deprecated, use `Open62541.UA_Argument_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_Argument_init(x)` to reset the type and its memory.
