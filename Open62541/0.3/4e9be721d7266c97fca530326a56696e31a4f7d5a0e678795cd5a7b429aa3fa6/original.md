```
Open62541.UA_VariableTypeAttributes_deleteMembers(x::Ptr{Open62541.UA_VariableTypeAttributes})
```

(deprecated, use `Open62541.UA_VariableTypeAttributes_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_VariableTypeAttributes_init(x)` to reset the type and its memory.
