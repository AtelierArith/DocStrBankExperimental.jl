```
Open62541.UA_ObjectAttributes_clear(x::Ptr{Open62541.UA_ObjectAttributes})
```

deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ObjectAttributes_init(x)` to reset the type and its memory. 
