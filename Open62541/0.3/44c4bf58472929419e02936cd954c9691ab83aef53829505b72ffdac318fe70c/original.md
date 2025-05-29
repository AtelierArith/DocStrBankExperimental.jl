```
UA_Server_readMinimumSamplingInterval(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, out::Ptr{UA_Double})
```

Uses the Server API to read the value of the attribute MinimumSamplingInterval  from the NodeId `nodeId` located on server `server`. The result is saved  into `out`.

Note that memory for `out` must be allocated by C before using this function.  This can be accomplished with `out = UA_Double_new()`. The  resulting object must be cleaned up via `UA_Double_delete(out::Ptr{UA_Double})`     after its use.
