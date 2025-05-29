```
UA_Server_writeValue(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Variant})
```

Uses the Server API to write the value `new_val` to the attribute Value  of the NodeId `nodeId` located on the `server`. 
