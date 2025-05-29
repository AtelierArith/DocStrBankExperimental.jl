```
Open62541.UA_ServiceFault_deleteMembers(x::Ptr{Open62541.UA_ServiceFault})
```

(deprecated, use `Open62541.UA_ServiceFault_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ServiceFault_init(x)` to reset the type and its memory.
