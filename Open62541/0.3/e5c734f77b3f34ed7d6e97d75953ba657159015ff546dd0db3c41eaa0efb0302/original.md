```
Open62541.UA_RationalNumber_deleteMembers(x::Ptr{Open62541.UA_RationalNumber})
```

(deprecated, use `Open62541.UA_RationalNumber_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_RationalNumber_init(x)` to reset the type and its memory.
