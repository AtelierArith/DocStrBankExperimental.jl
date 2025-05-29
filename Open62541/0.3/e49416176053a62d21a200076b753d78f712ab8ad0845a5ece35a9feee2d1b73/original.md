```
Open62541.UA_EventNotificationList_deleteMembers(x::Ptr{Open62541.UA_EventNotificationList})
```

(deprecated, use `Open62541.UA_EventNotificationList_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_EventNotificationList_init(x)` to reset the type and its memory.
