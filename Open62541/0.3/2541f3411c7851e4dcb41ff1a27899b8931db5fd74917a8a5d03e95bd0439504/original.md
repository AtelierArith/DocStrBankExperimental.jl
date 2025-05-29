```
Open62541.UA_Annotation_copy(src::Ptr{Open62541.UA_Annotation}, dst::Ptr{Open62541.UA_Annotation})::UA_STATUSCODE
Open62541.UA_Annotation_copy(src::Open62541.UA_Annotation, dst::Ptr{Open62541.UA_Annotation})::UA_STATUSCODE
```

Copy the content of the source object `src` to the destination object `dst`. Returns `UA_STATUSCODE_GOOD` or `UA_STATUSCODE_BADOUTOFMEMORY`.
