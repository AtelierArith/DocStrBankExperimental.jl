```
UA_Server_writeWriteMask(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_UInt32})
```

Uses the Server API to write the value `new_val` to the attribute WriteMask  of the NodeId `nodeId` located on the `server`. 
