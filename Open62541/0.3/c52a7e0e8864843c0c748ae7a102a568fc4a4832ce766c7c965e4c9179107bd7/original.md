```
Open62541.UA_NotificationMessage_deleteMembers(x::Ptr{Open62541.UA_NotificationMessage})
```

(deprecated, use `Open62541.UA_NotificationMessage_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_NotificationMessage_init(x)` to reset the type and its memory.
