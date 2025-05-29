```
UA_Server_writeEventNotifier(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Byte})
```

Uses the Server API to write the value `new_val` to the attribute EventNotifier  of the NodeId `nodeId` located on the `server`. 
