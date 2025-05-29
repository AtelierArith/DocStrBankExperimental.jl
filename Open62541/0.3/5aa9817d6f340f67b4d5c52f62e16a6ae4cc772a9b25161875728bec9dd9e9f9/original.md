```
Open62541.UA_ResponseHeader_deleteMembers(x::Ptr{Open62541.UA_ResponseHeader})
```

(deprecated, use `Open62541.UA_ResponseHeader_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ResponseHeader_init(x)` to reset the type and its memory.
