```
UA_Server_writeDataType(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_NodeId})
```

Uses the Server API to write the value `new_val` to the attribute DataType  of the NodeId `nodeId` located on the `server`. 
