```
UA_Server_writeBrowseName(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_QualifiedName})
```

Uses the Server API to write the value `new_val` to the attribute BrowseName  of the NodeId `nodeId` located on the `server`. 
