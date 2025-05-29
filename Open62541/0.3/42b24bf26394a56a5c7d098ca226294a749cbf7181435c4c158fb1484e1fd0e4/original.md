```
Open62541.UA_ElementOperand_deleteMembers(x::Ptr{Open62541.UA_ElementOperand})
```

(deprecated, use `Open62541.UA_ElementOperand_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ElementOperand_init(x)` to reset the type and its memory.
