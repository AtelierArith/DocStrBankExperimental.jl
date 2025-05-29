```
UA_Server_writeDataValue(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_DataValue})
```

Uses the Server API to write the value `new_val` to the attribute DataValue  of the NodeId `nodeId` located on the `server`. 
