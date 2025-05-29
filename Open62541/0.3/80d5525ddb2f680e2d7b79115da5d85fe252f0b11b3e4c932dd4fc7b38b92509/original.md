```
Open62541.UA_ThreeDVector_deleteMembers(x::Ptr{Open62541.UA_ThreeDVector})
```

(deprecated, use `Open62541.UA_ThreeDVector_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ThreeDVector_init(x)` to reset the type and its memory.
