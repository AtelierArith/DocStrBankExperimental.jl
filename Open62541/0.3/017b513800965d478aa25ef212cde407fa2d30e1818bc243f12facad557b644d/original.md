```
Open62541.UA_ExtensionObject_clear(x::Ptr{Open62541.UA_ExtensionObject})
```

deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_ExtensionObject_init(x)` to reset the type and its memory. 
