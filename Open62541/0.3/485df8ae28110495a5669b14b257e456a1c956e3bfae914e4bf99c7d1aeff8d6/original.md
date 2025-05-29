```
UA_Server_readWriteMask(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_UInt32})
```

Uses the Server API to read the value of the attribute WriteMask  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_UInt32_new()`. The  resulting object must be cleaned up via `UA_UInt32_delete(out::Ptr{UA_UInt32})`     after its use.
