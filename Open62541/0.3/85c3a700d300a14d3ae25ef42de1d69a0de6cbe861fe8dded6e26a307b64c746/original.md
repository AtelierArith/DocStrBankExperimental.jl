```
UA_Server_readNodeClass(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_NodeClass})
```

Uses the Server API to read the value of the attribute NodeClass  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_NodeClass_new()`. The  resulting object must be cleaned up via `UA_NodeClass_delete(out::Ptr{UA_NodeClass})`     after its use.
