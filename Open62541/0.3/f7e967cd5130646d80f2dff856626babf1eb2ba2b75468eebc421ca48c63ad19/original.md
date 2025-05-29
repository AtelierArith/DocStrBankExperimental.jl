```
Open62541.UA_String_deleteMembers(x::Ptr{Open62541.UA_String})
```

(deprecated, use `Open62541.UA_String_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_String_init(x)` to reset the type and its memory.
