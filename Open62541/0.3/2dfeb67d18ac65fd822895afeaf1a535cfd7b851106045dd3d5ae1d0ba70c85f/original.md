```
Open62541.UA_EnumDescription_deleteMembers(x::Ptr{Open62541.UA_EnumDescription})
```

(deprecated, use `Open62541.UA_EnumDescription_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_EnumDescription_init(x)` to reset the type and its memory.
