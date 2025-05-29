```
UA_Server_readEventNotifier(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_Byte})
```

Uses the Server API to read the value of the attribute EventNotifier  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_Byte_new()`. The  resulting object must be cleaned up via `UA_Byte_delete(out::Ptr{UA_Byte})`     after its use.
