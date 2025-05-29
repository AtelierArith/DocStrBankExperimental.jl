```
Open62541.UA_AttributeOperand_deleteMembers(x::Ptr{Open62541.UA_AttributeOperand})
```

(deprecated, use `Open62541.UA_AttributeOperand_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_AttributeOperand_init(x)` to reset the type and its memory.
