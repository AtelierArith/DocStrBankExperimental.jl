```
UA_Server_writeDisplayName(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_LocalizedText})
```

Uses the Server API to write the value `new_val` to the attribute DisplayName  of the NodeId `nodeId` located on the `server`. 
