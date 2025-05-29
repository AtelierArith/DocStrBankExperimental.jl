```
UA_Server_readDescription(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_LocalizedText})
```

Uses the Server API to read the value of the attribute Description  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_LocalizedText_new()`. The  resulting object must be cleaned up via `UA_LocalizedText_delete(out::Ptr{UA_LocalizedText})`     after its use.
