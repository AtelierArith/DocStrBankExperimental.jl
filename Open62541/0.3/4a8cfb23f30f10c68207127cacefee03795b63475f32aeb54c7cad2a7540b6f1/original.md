```
Open62541.UA_DiagnosticInfo_deleteMembers(x::Ptr{Open62541.UA_DiagnosticInfo})
```

(deprecated, use `Open62541.UA_DiagnosticInfo_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_DiagnosticInfo_init(x)` to reset the type and its memory.
