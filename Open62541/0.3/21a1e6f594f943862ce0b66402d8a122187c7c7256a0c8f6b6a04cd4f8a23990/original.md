```
UA_Server_readBrowseName(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_QualifiedName})
```

Uses the Server API to read the value of the attribute BrowseName  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_QualifiedName_new()`. The  resulting object must be cleaned up via `UA_QualifiedName_delete(out::Ptr{UA_QualifiedName})`     after its use.
