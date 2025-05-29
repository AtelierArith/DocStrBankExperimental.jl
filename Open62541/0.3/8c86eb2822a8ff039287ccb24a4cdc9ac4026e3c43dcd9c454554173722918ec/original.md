```
Open62541.UA_Argument_clear(x::Ptr{Open62541.UA_Argument})
```

deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_Argument_init(x)` to reset the type and its memory. 
