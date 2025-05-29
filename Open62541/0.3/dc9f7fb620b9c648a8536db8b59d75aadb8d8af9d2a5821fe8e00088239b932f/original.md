```
Open62541.UA_PubSubGroupDataType_deleteMembers(x::Ptr{Open62541.UA_PubSubGroupDataType})
```

(deprecated, use `Open62541.UA_PubSubGroupDataType_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_PubSubGroupDataType_init(x)` to reset the type and its memory.
