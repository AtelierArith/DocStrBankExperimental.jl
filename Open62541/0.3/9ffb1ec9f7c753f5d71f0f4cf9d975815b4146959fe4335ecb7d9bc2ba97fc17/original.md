```
Open62541.UA_Annotation_deleteMembers(x::Ptr{Open62541.UA_Annotation})
```

(deprecated, use `Open62541.UA_Annotation_clear(x)` instead) deletes the dynamically allocated content of the object `x` and calls `Open62541.UA_Annotation_init(x)` to reset the type and its memory.
