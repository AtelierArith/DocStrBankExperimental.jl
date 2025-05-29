```
UA_NODEID_NUMERIC(nsIndex::Integer, identifier::Integer)::Ptr{UA_NodeId}
```

creates a `UA_NodeId` object with namespace index `nsIndex` and numerical identifier `identifier`. Memory is allocated by C and needs to be cleaned up using `UA_NodeId_delete(x::Ptr{UA_NodeId})` after the object is not used anymore.
