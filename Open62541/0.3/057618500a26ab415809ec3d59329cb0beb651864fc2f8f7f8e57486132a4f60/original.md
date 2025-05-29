```
UA_Server_readNodeId(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_NodeId})
```

Uses the Server API to read the value of the attribute NodeId  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_NodeId_new()`. The  resulting object must be cleaned up via `UA_NodeId_delete(out::Ptr{UA_NodeId})`     after its use.
