```
UA_Server_writeValueRank(server::Ptr{UA_Server}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Int32})
```

Uses the Server API to write the value `new_val` to the attribute ValueRank  of the NodeId `nodeId` located on the `server`. 
