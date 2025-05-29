```
Open62541.UA_StatusChangeNotification_deleteMembers(x::Ptr{Open62541.UA_StatusChangeNotification})
```

(deprecated, use `Open62541.UA_StatusChangeNotification_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_StatusChangeNotification_init(x)` to reset the type and its memory.
