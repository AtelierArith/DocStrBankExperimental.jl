```
Open62541.UA_DataValue_clear(x::Ptr{Open62541.UA_DataValue})
```

deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_DataValue_init(x)` to reset the type and its memory. 
