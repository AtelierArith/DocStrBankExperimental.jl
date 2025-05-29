```
Open62541.UA_GenericAttributeValue_deleteMembers(x::Ptr{Open62541.UA_GenericAttributeValue})
```

(deprecated, use `Open62541.UA_GenericAttributeValue_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_GenericAttributeValue_init(x)` to reset the type and its memory.
