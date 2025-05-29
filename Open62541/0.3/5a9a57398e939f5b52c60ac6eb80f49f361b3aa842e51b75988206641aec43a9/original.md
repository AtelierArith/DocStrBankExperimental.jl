```
UA_Server_writeAccessLevel(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

Uses the Server API to write the value `new_val` to the attribute AccessLevel  of the NodeId `nodeId` located on the `server`. 
