```
UA_Client_writeValueRankAttribute(client::Ptr{UA_Client}, nodeId::Ptr{UA_NodeId}, new_val::Ptr{UA_Int32})
```

Uses the UA Client API to write the value `new_val` to the attribute ValueRank of the NodeId `nodeId` accessed through the client `client`. 
