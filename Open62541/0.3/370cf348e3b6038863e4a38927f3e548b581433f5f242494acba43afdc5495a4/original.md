```
UA_NODEID_BYTESTRING(nsIndex::Integer, identifier::AbstractString)::Ptr{UA_NodeId}
UA_NODEID_BYTESTRING(nsIndex::Integer, identifier::Ptr{UA_ByteString})::Ptr{UA_NodeId}
```

creates a `UA_NodeId` object with namespace index `nsIndex` and bytestring identifier `identifier` (which can be a string or UA_ByteString).

Memory is allocated by C and needs to be cleaned up using `UA_NodeId_delete(x::Ptr{UA_NodeId})` after the object is not used anymore.
