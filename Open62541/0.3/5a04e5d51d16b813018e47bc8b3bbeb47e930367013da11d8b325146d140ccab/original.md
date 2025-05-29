```
UA_NODEID_STRING_ALLOC(nsIndex::Integer, identifier::AbstractString)::Ptr{UA_NodeId}
UA_NODEID_STRING_ALLOC(nsIndex::Integer, identifier::Ptr{UA_String})::Ptr{UA_NodeId}
```

creates a `UA_NodeId` object with namespace index `nsIndex` and string identifier `identifier`.

Memory is allocated by C and needs to be cleaned up using `UA_NodeId_delete(x::Ptr{UA_NodeId})` after the object is not used anymore.
