```
Open62541.UA_UserTokenPolicy_deleteMembers(x::Ptr{Open62541.UA_UserTokenPolicy})
```

(deprecated, use `Open62541.UA_UserTokenPolicy_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_UserTokenPolicy_init(x)` to reset the type and its memory.
