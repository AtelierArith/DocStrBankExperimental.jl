```
Open62541.UA_GenericAttributes_deleteMembers(x::Ptr{Open62541.UA_GenericAttributes})
```

(deprecated, use `Open62541.UA_GenericAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_GenericAttributes_init(x)` to reset the type and its memory.
