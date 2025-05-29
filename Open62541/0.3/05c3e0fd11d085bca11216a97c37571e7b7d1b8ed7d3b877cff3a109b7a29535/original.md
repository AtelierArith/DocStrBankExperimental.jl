```
Open62541.UA_ParsingResult_deleteMembers(x::Ptr{Open62541.UA_ParsingResult})
```

(deprecated, use `Open62541.UA_ParsingResult_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ParsingResult_init(x)` to reset the type and its memory.
