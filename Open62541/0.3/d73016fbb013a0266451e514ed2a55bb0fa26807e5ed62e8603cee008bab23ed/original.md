```
Open62541.UA_StructureDescription_deleteMembers(x::Ptr{Open62541.UA_StructureDescription})
```

(deprecated, use `Open62541.UA_StructureDescription_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_StructureDescription_init(x)` to reset the type and its memory.
