```
Open62541.UA_OpenFileMode_deleteMembers(x::Ptr{Open62541.UA_OpenFileMode})
```

(deprecated, use `Open62541.UA_OpenFileMode_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_OpenFileMode_init(x)` to reset the type and its memory.
