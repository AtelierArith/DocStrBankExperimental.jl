```
Open62541.UA_PubSubState_deleteMembers(x::Ptr{Open62541.UA_PubSubState})
```

(deprecated, use `Open62541.UA_PubSubState_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_PubSubState_init(x)` to reset the type and its memory.
