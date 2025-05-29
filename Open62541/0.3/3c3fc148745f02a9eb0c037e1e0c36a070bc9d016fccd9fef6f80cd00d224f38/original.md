```
UA_NODEID_GUID(nsIndex::Integer, identifier::AbstractString)::Ptr{UA_NodeId}
UA_NODEID_GUID(nsIndex::Integer, identifier::Ptr{UA_Guid})::Ptr{UA_NodeId}
```

creates a `UA_NodeId` object by with namespace index `nsIndex` and an identifier `identifier` based on a globally unique id (`UA_Guid`) that can be supplied as a string (which will be parsed) or as a valid `Ptr{UA_Guid}`.

Memory is allocated by C and needs to be cleaned up using `UA_NodeId_delete(x::Ptr{UA_NodeId})` after the object is not used anymore.
